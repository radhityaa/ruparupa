Add this code on your web config :

```
location / {
  try_files $uri $uri/ /index.php?$query_string;
}
```
