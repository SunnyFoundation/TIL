# ServerAction

⚡️ Your code executed as server without fetch  you can just use ‘use server’







``` typescript 

'use client';

export default function Page() {
  async function handleSubmit(formData: FormData) {
    'use server'; // 이 함수는 서버에서 실행됨!

    const name = formData.get('name');

    console.log('서버에서 받은 이름:', name); // 서버 로그에 출력됨
  }

  return (
    <form action={handleSubmit}>
      <input name="name" placeholder="이름 입력" required />
      <button type="submit">전송</button>
    </form>
  );
}

```
