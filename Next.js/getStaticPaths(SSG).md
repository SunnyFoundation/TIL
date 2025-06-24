# getStaticPaths









``` typescript 
1. When you wanna dynamic url parameter page made SSG  
2. then use getStaticPaths
3. it return paths,fallback
4. path is value of url parameter
5. fallback is if we made params 1,2,3 and the other url parameter value you control 


export const getStaticPaths =  () => {
    return {
      paths : [
        { params : {id : "1"} },
        { params : {id : "2"} },
        { params : {id : "3"} },
      ],
      fallback : true, // it means the other parameter show up when user request 
    };
};


export const getStaticProps = async (context : GetStaticPropsContext) => {
  const id = context.params!.id; 
  const movie = await fetchOneMovie(Number(id));

  if (!movie) {
    return {notFound : true};
  }


  return {
    props : {movie},
  };
};


export default function Page({movie} : InferGetStaticPropsType<typeof getStaticProps>) {

```
