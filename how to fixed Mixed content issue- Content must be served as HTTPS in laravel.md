fix error https make laragon ssl in laravel

example error:
prabayar:841 
 Mixed Content: The page at 'https://ppob.ayasyatech.online/product/prabayar' was loaded over HTTPS, but requested an insecure XMLHttpRequest endpoint 'http://ppob.ayasyatech.online/product/prabayar?draw=1&columns%5B0%5D%5Bdata…art=0&length=10&search%5Bvalue%5D=&search%5Bregex%5D=false&_=1718594214063'. This request has been blocked; the content must be served over HTTPS.

add script in :
App\Providers\AppServiceProvider.php

```php
if(env('APP_ENV') !== 'local')
{
  URL::forceScheme('https');
}
```
