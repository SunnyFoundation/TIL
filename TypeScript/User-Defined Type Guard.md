# User-Defined Type Guard








``` typescript 
type Dog = {
  name: string;
  bark: () => void;
};

type Cat = {
  name: string;
  meow: () => void;
};

type Animal = Dog | Cat;

// 사용자 정의 타입 가드
function isDog(animal: Animal): animal is Dog {
  return (animal as Dog).bark !== undefined;  
}

// 사용 예시
const pet: Animal = { name: "Buddy", bark: () => console.log("멍!"), meow: () => console.log("야옹!") };

if (isDog(pet)) {
  // TypeScript는 여기서 pet을 Dog로 인식해
  pet.bark(); // 안전하게 사용 가능
} else {
  pet.meow(); // 
}
```

