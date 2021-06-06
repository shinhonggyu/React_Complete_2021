**data fetching with React hooks**

```js
const App = () => {
  const [data, setData] = useState({ hits: [] });

  // useEffect(() => {
  //   fetch('https://hn.algolia.com/api/v1/search?query=redux')
  //     .then((res) => res.json())
  //     .then((result) => setData(result));
  // });

  useEffect(() => {
    const fetchData = async () => {
      const result = await axios(
        'https://hn.algolia.com/api/v1/search?query=redux'
      );
      setData(result.data);
    };

    fetchData();
  }, []);

  return (
    <ul>
      {data.hits.map((item) => (
        <li key={item.objectID}>
          <a href={item.url}>{item.title}</a>
        </li>
      ))}
    </ul>
  );
};
```

**useEffect complete**
