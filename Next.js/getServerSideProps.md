# getServerSideProps









``` typescript 
1. It excuted from server 
2. When user enter  “/“
3.  getServerSideProps excuted 
4.  index.tsx get props from getServerSideProps
5.  index.tsx send itself to _app.tsx in the Component


export const getServerSideProps = async () => {

  const allMovie = await fetchMovie();
  const recoMovie = await fetchRandomMovie();

  return { 
    props : {
      allMovie,
      recoMovie,
    },
  }
}


export default function Home({allMovie,recoMovie}) : InferGetServerSidePropsType<typeof getServerSideProps> {


```
