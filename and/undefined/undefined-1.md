# 파일 다운로드

```text

    const axiosOptions = {
    method,
    url,
    params,
    responseType: 'blob',
  };
  if (method === 'POST') {
    axiosOptions.data = params;
    delete axiosOptions['params'];
  }
  const { data, headers } = await axios(axiosOptions);
  const blob = new Blob([data]);
```



