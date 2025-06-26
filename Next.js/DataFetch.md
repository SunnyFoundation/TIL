# DataFetch

⚡️ You have to put async keyword in your component that’s it !







``` typescript 


async function RecoMovies() {

  const response = await fetch(
    `http://localhost:12345/movie/random`,
    {
      next: { revalidate: 3 },
    }
  );
  if (!response.ok) {
    return <div>Error!..</div>;
  }

  const recoMovies: MovieData[] = await response.json();


```
