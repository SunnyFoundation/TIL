# getStaticProps









``` typescript 
1. When you  do npm run build then
2. The page is created so user can watch your website 
3. It was created because bad thing about SSR
4. That server status is bad then user received  your site So slowly
5. But the SSG way your website only can showed when npm run build so 
6. It is no matter with server status 
7. but it is only useful when page is not dynamic
8. Because it is excuted only build process
9.  so it is not updated when user request your page
10. that means SSG page is static 


export const getStaticProps = async () => {

  const [allMovie,recoMovie] = await Promise.all([fetchMovie(),fetchRandomMovie()]);

 

  return { 
    props : {
      allMovie,
      recoMovie,
    },
  }
}


export default function Home({
  allMovie,recoMovie,
} : InferGetStaticPropsType<typeof getStaticProps>) {

```
