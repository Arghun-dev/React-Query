# React-Query

As we know react-query is used for fetching data from the server and saving that data user local cache. 

But you can also use it to make it `global state management` library like redux and save data, any data in local cahce and use it every where.

To do that I create a `Hook` => `useRQGlobalState`.

`You always need to wrap your app with QueryClient`. to be able to use react-query.


```js
import { QueryClient, useQuery } from 'react-query';


const useRQGlobalState = (key, initialData) => [
  useQuery(key, () => initialData, {
    enabled: false,
    initialData
  }).data,
  
  (value) => client.setQueryData(key, value)
]


const StateEditor = () => {
  const [value, setValue] = useRQGlobalState("sharedText", "");
  
  return <input value={value} onChange={(e) => setValue(e.target.value)} />
}

const StateViewer = () => {
  const [value] = useRQGlobalState("sharedText", "");
  
  return <p>{value}</p>
}
```
