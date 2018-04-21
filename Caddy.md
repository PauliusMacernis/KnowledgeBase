- **Explain the following code found in Caddyfile (configuration file of Caddy):**  
```
0.0.0.0
root /srv/app/public
gzip
fastcgi / 127.0.0.1:9000 php
rewrite {
  regexp .*
  ext /
  to /index.php?{query}
}

header / -Server

log stdout
errors stdout
on startup php-fpm --nodaemonize
```
The first line defines the site address of our application, which is `0.0.0.0`, or `localhost`. We can use this line to specify the site address, which can take many forms. To learn
more, you should check out the HTTP Caddyfile (https://caddyserver.com/docs/http-caddyfile) documentation.  
The next line, `gzip`, is known as a Caddy directive. We configure the `gzip` directive to use the defaults, but you could customize the configuration with a block:
```
gzip {
  ext
  not
  level
  min_length
  }
```
Next, we are defining a FastCGI proxy so we can communicate with PHP-FPM.  
After FastCGI, we define a main rewrite (https://caddyserver.com/docs/rewrite) rule that rewrites everything to our app's `public/index.php` file.  
We wrap up the `Caddyfile` by sending access and error logs to stdout and stderr.  
The last line starts PHP-FPM in the background with `on startup` event. The `startup` event is triggered just before the server starts listening.  

Read more:  
https://caddyserver.com/tutorial/caddyfile  
https://caddyserver.com/docs/http-caddyfile  
https://caddyserver.com/docs/rewrite  
