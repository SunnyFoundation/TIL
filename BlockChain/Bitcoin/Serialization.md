# Serialization
⚡️ turn object into byteStream




## Base58

```python
 def encode_base58(s):
    count = 0
    for c in s:  # <1>
        if c == 0:
            count += 1
        else:
            break
    num = int.from_bytes(s, 'big')
    prefix = '1' * count
    result = ''
    while num > 0:  # <2>
        num, mod = divmod(num, 58)
        result = BASE58_ALPHABET[mod] + result
    return prefix + result  # <3>



sec = "02933ec2d2b111b92737ec12f1c5d20f3233a0ad21cd8b36d0bca7a0cfa5cb8701"
sec_to_bytes = bytes.fromhex(sec)
print(encode_base58(sec_to_bytes))   # mNRBP9AM1HtBoBxWcT6qU51HFc887Q3DDGrc8nWQwPUC
print(encode_base58_checksum(sec_to_bytes))   # 61LXuQFciEDZnZB9EdA5NPAHbm6f7iFQbrHioRfgi4YNkdZP6Q





def encode_base58_checksum(b):
    return encode_base58(b + hash256(b)[:4])



```

## SEC

```python
    def sec(self, compressed=True):
        if compressed:
            if self.y.num % 2 == 0:
                return b'\x02' + self.x.num.to_bytes(32, 'big')
            else:
                return b'\x03' + self.x.num.to_bytes(32, 'big')
        else:
            return b'\x04' + self.x.num.to_bytes(32, 'big') + \
                self.y.num.to_bytes(32, 'big')



priv = PrivateKey(5001)
sec = priv.point.sec().hex()
print(sec) 02933ec2d2b111b92737ec12f1c5d20f3233a0ad21cd8b36d0bca7a0cfa5cb8701


```



## Der

```python

class Signature:


    def der(self):
        rbin = self.r.to_bytes(32, byteorder='big')
        rbin = rbin.lstrip(b'\x00')
        if rbin[0] & 0x80:
            rbin = b'\x00' + rbin
        result = bytes([2, len(rbin)]) + rbin  # <1>
        sbin = self.s.to_bytes(32, byteorder='big')
        sbin = sbin.lstrip(b'\x00')
        if sbin[0] & 0x80:
            sbin = b'\x00' + sbin
        result += bytes([2, len(sbin)]) + sbin
        return bytes([0x30, len(result)]) + result




 r = 0x37206a0610995c58074999cb9767b87af4c4978db68c06e8e6e81d282047a7c6
 s = 0x8ca63759c1157ebeaec0d03cecca119fc9a75bf8e6d0fa65c841c8e2738cdaec
 sig = Signature(r,s)
print(sig.der().hex())
 3045022037206a0610995c58074999cb9767b87af4c4978db68c06e8e6e81d282047a7c60221008ca63759c1157ebeaec0d03cecca119fc9a75bf8e6d0fa65c841c8e2738cdaec


```


## Address

```python

class S256Point(Point):

    def address(self, compressed=True, testnet=False):
        h160 = self.hash160(compressed)
        if testnet:
            prefix = b'\x6f'
        else:
            prefix = b'\x00'
        return encode_base58_checksum(prefix + h160


passphrase = b'sunkim1055@gmail.com my sercret'
secret = little_endian_to_int(passphrase)
priv = PrivateKey(secret)
print(priv.point.address(testnet=True))  moMgoV8ouE3i6cQ96PNRcQ63jPonhztGME


```



