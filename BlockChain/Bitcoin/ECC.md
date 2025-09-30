# 🔐 Elliptic Curve Cryptography
* 1️⃣ Definition
* 2️⃣ Scala Multiple
* 6️⃣ S256Field
* 7️⃣ S256Point
* 8️⃣ Create Signature
* 9️⃣ Verify Signature






## Definition
```
Randome Point G * your private key  in Elliptic Curve you can take Public Key
The Key is  k*G = P is super easy But  ? * G = P  How to get " ? " ?   that is super difficult
This is ECC 

ECC는 타원곡선의 점 덧셈 연산을 기반으로 한 공개키 암호 방식이다
kG = P 꼴의 문제에서 k를 구하기 어려운 성질(이산로그문제)를 이용한다. 
이 성질 덕분에 서명(ECDSA)을 안전하게 생성하고 검증할수있다.

```

## Scala Multiple
```python

prime = 223
x = FieldElement(15,prime)
y = FieldElement(86,prime)
a = FieldElement(0,prime)
b = FieldElement(7,prime)
p1 = Point(x,y,a,b)
p2 = Point(x,y,a,b)
print(7*p1) //  infinity 


class Point:

  def __rmul__(self,coefficient):
     coef = coefficient
     current = self
     result = self.__class__(None,None,self.a,self,b)
     while coef:
       if coef & 1 :
         result += current
       current += current
       coef >>= 1
     return result


 def __add__(self,other):
    if self == other:
      s = ( 3 * self.x ** 2 + self.a) / (2 * self.y)
      x = s**2  - 2 * self.x
      y = s * (self.x - x ) - self.y
      return self.__class__(x,y,self.a,self.b)



class FieldElement:

  def __rmul__(self,coefficient):
     num = (self.num * cofficient) % self.prime
     return self.__class__(num = num , prime=self.prime)




```




## Create Signature
```python

from FieldElement import FieldElement
from Point import Point
from secp256k1 import S256Point
from helper import hash256
from random import randint






## Create Signature
```python

from FieldElement import FieldElement
from Point import Point
from secp256k1 import S256Point
from helper import hash256
from random import randint




 # Special Point In Secp256K1
G = S256Point(0x79be667ef9dcbbac55a06295ce870b07029bfcdb2dce28d959f2815b16f81798,0x483ada7726a3c4655da4fbfc0e1108a8fd17b448a68554199c47d08ffb10d4b8)
 # order
N = 0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141


# Private_key
e = int.from_bytes(hash256(b'my secret'), 'big') 



#  Hassing Message 
z = int.from_bytes(hash256(b'my message'), 'big')  




class Signature:


    def __init__(self,r,s):
        self.r = r
        self.s = s


    def __repr__(self):
        return "Signature({:x},{:x}).".format(self.r,self.s)
       
        

class PrivateKey:


    def __init__(self, secret):

        #  개인 키
        self.secret = secret

        #  공개 키
        self.point = secret * G #1


    # 개인키를 16진수로 변환 
    def hex(self):
        return '{:x}'.format(self.secret).zfill(64)
    
    # 메시지 해시 z 를 받아서 서명함 
    def sign(self, z):
        # 랜덤값 생성
        k = randint(0, N) 
        
        # r 값 생성
        r = (k * G).x.num
        
        # k 역원 구하기 
        k_inv = pow(k, N-2, N) #3
        
        # 서명 값 구하기 
        s = (z + r * self.secret) * k_inv % N
        
        if s > N/2: #4
            s = N - s
            
        # 서명 값 리턴 
        return Signature(r, s)
    


private_key = PrivateKey(e)  # PrivateKey 객체 생성
signature = private_key.sign(z)  # sign() 호출 → Signature 객체 리턴


print(signature)  # Signature.__repr__ 덕분에 r,s 값 예쁘게 출력

```





## Verify Signature
```python

from FieldElement import FieldElement
from Point import Point



P = 2**256 - 2**32 - 977
A = 0
B = 7
N = 0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141


class S256Field(FieldElement):
	def __init__(self, num, prime=None):
		super().__init__(num=num, prime=P)
	
	def __repr__(self):
		return '{:x}'.format(self.num).zfill(64)
	

class S256Point(Point):
	
	def __init__(self, x, y, a=None, b=None):
		a, b = S256Field(A), S256Field(B)
		if type(x) == int :
			super().__init__(x=S256Field(x),y=S256Field(y),a=a,b=b)
		else :
			super().__init__(x=x,y=y,a=a,b=b)
	def __rmul__(self,coefficient):
		coef = coefficient % N
		return super().__rmul__(coef)
	
	def verify(self, z, sig):
		
		s_inv = pow(sig.s, N-2, N)
		u = z * s_inv % N
		v = sig.r * s_inv % N
		total = u * G + v * self
		return total.x.num == sig.r
		
	

	
		
G = S256Point(
    0x79be667ef9dcbbac55a06295ce870b07029bfcdb2dce28d959f2815b16f81798,
    0x483ada7726a3c4655da4fbfc0e1108a8fd17b448a68554199c47d08ffb10d4b8
)


```
