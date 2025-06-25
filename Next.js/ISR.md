# getStaticPaths









``` typescript 
1. SSG is page has been rendering
2. When you npm run build 
3. But SSG is not re-rendering after you build
4. Here is ISR came from 
5. ISR is After time has gone re-rendering auto


 export const getStaticProps = async () => {

  const [allMovie,recoMovie] = await Promise.all([fetchMovie(),fetchRandomMovie()]);

 

  return { 
    props : {
      allMovie,
      recoMovie,
    },
    revalidate : 3,  // this part re-rendering per 3 second 
  }
}


```
