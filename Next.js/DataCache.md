## DataCache

⚡️ Your component will be cached 


``` typescript
async function RecoMovies() {

  const response = await fetch(
    `http://localhost:12345/movie/random`,
    {
      cache: "force-cache"
    }
  );
  if (!response.ok) {
    return <div>Error!..</div>;
  }

  const recoMovies: MovieData[] = await response.json();
  '''
