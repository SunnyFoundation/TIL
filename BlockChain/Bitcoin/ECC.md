# 🔐 Elliptic Curve Cryptography
*  Definition
*  A
*  B
*  P
*  N
*  G
*  S256Field
*  S256Point
*  Signature
*  Privatekey
*  Excute Code






## Definition
```
Randome Point G * your private key  in Elliptic Curve you can take Public Key
The Key is  k*G = P is super easy But  ? * G = P  How to get " ? " ?   that is super difficult
This is ECC 

ECC는 타원곡선의 점 덧셈 연산을 기반으로 한 공개키 암호 방식이다
kG = P 꼴의 문제에서 k를 구하기 어려운 성질(이산로그문제)를 이용한다. 
이 성질 덕분에 서명(ECDSA)을 안전하게 생성하고 검증할수있다.

```

## A
```python

  
A = 0

```




## B
```python
B = 7




```


## P
```python
P = 2**256 - 2**32 - 977




```


## N 
```python
N = 0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141

```

## G
```python
G = S256Point(
    0x79be667ef9dcbbac55a06295ce870b07029bfcdb2dce28d959f2815b16f81798,
    0x483ada7726a3c4655da4fbfc0e1108a8fd17b448a68554199c47d08ffb10d4b8
)

```


## S256Field
```python

class S256Field(FieldElement):

    def __init__(self, num, prime=None):
        super().__init__(num=num, prime=P)

    def __repr__(self):
        return '{:x}'.format(self.num).zfill(64)

```


## S256Point
```python


class S256Point(Point):

    def __init__(self, x, y, a=None, b=None):
        a, b = S256Field(A), S256Field(B)
        if type(x) == int:
            super().__init__(x=S256Field(x), y=S256Field(y), a=a, b=b)
        else:
            super().__init__(x=x, y=y, a=a, b=b)  

    def __repr__(self):
        if self.x is None:
            return 'S256Point(infinity)'
        else:
            return 'S256Point({}, {})'.format(self.x, self.y)

    # tag::source8[]
    def __rmul__(self, coefficient):
        coef = coefficient % N  # <1>
        return super().__rmul__(coef)
    
    def verify(self, z, sig):
        s_inv = pow(sig.s, N - 2, N)  # <1>
        u = z * s_inv % N  # <2>
        v = sig.r * s_inv % N  # <3>
        total = u * G + v * self  # <4>
        return total.x.num == sig.r  # <5>
    
```


## Signature
```python


class Signature:

    def __init__(self, r, s):
        self.r = r
        self.s = s

    def __repr__(self):
        return 'Signature({:x},{:x})'.format(self.r, self.s)
    

    
```

## Privatekey
```python



class PrivateKey:

    def __init__(self, secret):
        self.secret = secret
        self.point = secret * G  # <1>

    def hex(self):
        return '{:x}'.format(self.secret).zfill(64)
    # end::source13[]

    # tag::source14[]
    def sign(self, z):
        k = self.deterministic_k(z)  # <1>
        r = (k * G).x.num
        k_inv = pow(k, N - 2, N)
        s = (z + r * self.secret) * k_inv % N
        if s > N / 2:
            s = N - s
        return Signature(r, s)
    

    def deterministic_k(self, z):
        k = b'\x00' * 32
        v = b'\x01' * 32
        if z > N:
            z -= N
        z_bytes = z.to_bytes(32, 'big')
        secret_bytes = self.secret.to_bytes(32, 'big')
        s256 = hashlib.sha256
        k = hmac.new(k, v + b'\x00' + secret_bytes + z_bytes, s256).digest()
        v = hmac.new(k, v, s256).digest()
        k = hmac.new(k, v + b'\x01' + secret_bytes + z_bytes, s256).digest()
        v = hmac.new(k, v, s256).digest()
        while True:
            v = hmac.new(k, v, s256).digest()
            candidate = int.from_bytes(v, 'big')
            if candidate >= 1 and candidate < N:
                return candidate  # <2>
            k = hmac.new(k, v + b'\x00', s256).digest()
            v = hmac.new(k, v, s256).digest()

    
```








## Excute Code
```python

pk = PrivateKey(randint(0, N))

private_key = pk.secret
publick_key = pk.point
z = randint(0, 2**256)
sig = pk.sign(z)
print(sig)
print(pk.point.verify(z,sig))


```
