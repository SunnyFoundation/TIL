# searchParams

⚡️ you can receive query string 







``` typescript 

  const searchParams = useSearchParams();
  const q = searchParams.get("q");

  useEffect(() => {
    setSearch(q || "");
  }, [q]);

```
