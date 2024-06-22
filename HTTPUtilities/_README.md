#### HTTP Utilities (`httpUtils.js`)

- **fetchWithTimeout**: Fetches data from a URL with a specified timeout.

```javascript {.line-numbers}
export const fetchWithTimeout = async (url, options = {}, timeout = 5000) => {
  const controller = new AbortController();
  const id = setTimeout(() => controller.abort(), timeout);
  const response = await fetch(url, { ...options, signal: controller.signal });
  clearTimeout(id);
  return response;
};
```
