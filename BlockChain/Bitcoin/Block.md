# Block
  ⚡️ List of Transctions that have 80 byes 


## __init__
```python

       def __init__(self, version, prev_block, merkle_root, timestamp, bits, nonce):
        self.version = version
        self.prev_block = prev_block
        self.merkle_root = merkle_root
        self.timestamp = timestamp
        self.bits = bits
        self.nonce = nonce
```


## parse
```python

    
    @classmethod
    def parse(cls, s):
        version = little_endian_to_int(s.read(4))
        prev_block = s.read(32)[::-1]  # network에서 읽을 때 big→little 변환
        merkle_root = s.read(32)[::-1]
        timestamp = little_endian_to_int(s.read(4))
        bits = s.read(4)
        nonce = s.read(4)
        return cls(version, prev_block, merkle_root, timestamp, bits, nonce)
```



## serialize
```python


    def serialize(self):
        version_bytes = int_to_little_endian(self.version, 4)
        prev_block_bytes = self.prev_block[::-1]  # little→big 복원
        merkle_root_bytes = self.merkle_root[::-1]
        timestamp_bytes = int_to_little_endian(self.timestamp, 4)
        bits_bytes = self.bits
        nonce_bytes = self.nonce
        return (
            version_bytes
            + prev_block_bytes
            + merkle_root_bytes
            + timestamp_bytes
            + bits_bytes
            + nonce_bytes
        )
```


## hash
```python
    def hash(self):
        s = self.serialize()
        sha = hash256(s)
        return sha[::-1]
```

## bip
```python
    def bip9(self):
        return self.version >> 29 == 0b001

    def bip91(self):
        return self.version >> 4 & 1 == 1

    def bip141(self):
        return self.version >> 1 & 1 == 1
```



## target
```python
      def target(self):
        return bits_to_target(self.bits)

```

## difficulty
```python
   def difficulty(self):
        lowest = 0xFFFF * 256 ** (0x1D - 3)
        return lowest / self.target()


```


## check_pow
```python
    def check_pow(self):
        proof = self.hash()
        target_value = self.target().to_bytes(32, "big")
        return proof < target_value

```


## calculate_new_bits
```python
  @staticmethod
    def calculate_new_bits(previous_bits, time_differential):
        if (
            time_differential > TWO_WEEKS * 4
        ):  # 시간차이가 8주보다 크다면 그냥 8주로 박음
            time_differential = TWO_WEEKS * 4
        if (
            time_differential < TWO_WEEKS // 4
        ):  # 시간차이가 3.5일보다 작으면 그냥 그냥 3.5일로 박음
            time_differential = TWO_WEEKS // 4
        new_target = bits_to_target(previous_bits) * time_differential // TWO_WEEKS
        return target_to_bits(new_target)

```


## mine
``` python
     def mine(self, start_nonce=0, max_nonce=0xFFFFFFFF):
        """
        채굴 시도 함수.
        nonce를 0부터 하나씩 증가시키며 check_pow()가 True가 될 때까지 반복.
        """
        target = self.target()
        print(f"Mining... target = {hex(target)}")

        start_time = time.time()
        for nonce in range(start_nonce, max_nonce):
            self.nonce = int_to_little_endian(nonce, 4)
            hash_value = hash256(self.serialize())
            # 비교 시 little-endian → big-endian으로 뒤집기
            if hash_value[::-1] < target.to_bytes(32, "big"):
                elapsed = time.time() - start_time
                print(f"✅ Found! Nonce = {nonce}, Hash = {hash_value[::-1].hex()}")
                print(f"Elapsed: {elapsed:.2f} sec")
                return nonce
            if nonce % 1000000 == 0:
                print(f"Checked nonce {nonce}... still mining")

        print("❌ No valid nonce found in range.")
        return None

```

