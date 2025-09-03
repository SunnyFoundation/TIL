```python
class Point:
    def __init__(self,x,y,a,b):
        self.x = x
        self.y = y
        self.a = a
        self.b = b



        if self.x == None or self.y == None :
           return 



        if self.y**2 != self.x**3 + a * x + b:
            raise ValueError('({}, {}) is not on the curve'.format(x,y))




    def __repr__(self):
        return f"Point({self.x}, {self.y})_Curve(a={self.a}, b={self.b})"




    def __eq__(self, other):
        return self.x == other.x and self.y == other.y and self.a == other.a and self.b == other.b




    def __add__(self,other):
         # 곡선이 다르면 오류
        if self.a != other.a or self.b != other.b:
            raise TypeError("points {},{} is not on the curve".format(x,y))
        
        # 무한점 처리
        if self.x == None:
            return other
        if other.x == None:
            return self
        
       # 서로 다른 점
        if self.x != other.x:
                s = (other.y - self.y) / (other.x - self.x)
                x = s**2 - self.x - other.x
                y = s * (self.x - x) - self.y
                return self.__class__(x,y,self.a,self.b)
        
         # 자기 자신과 더할 때
        if self == other :                
            s = (3 * self.x**2 + self.a) / (2 * self.y)
            x = s**2 - 2 * self.x
            y = s * (self.x - x) - self.y
            return self.__class__(x, y, self.a, self.b)
        
        # x 좌표가 같고 y 좌표가 반대이면 무한점 반환
        if self.x == other.x and self.y == -other.y:
            return self.__class__(None, None, self.a, self.b)


        
        ## self.y는 FieldElement 객체이므로 0과 비교 못함 그래서 self.x를 곱해서 FieldElement 타입으로 바꿔줌
        if self == other and self.y == 0 * self.x:
            return self.__class__(None, None, self.a, self.b)




p1 = Point(-1,-1,5,7)
p2 = Point(-1,1,5,7)


print(p1+p2)


```
