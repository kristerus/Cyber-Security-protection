[[ETHICAL-HACKING]]


## What is TLS?
TLS== Transport Layer Security is a cryptographic protocol designed to allow client-server communication accross a network while preventing tampering and eavesdropping.
HTTPS uses the TLS protocol.

## Unencrypted communication 
->http sites. Potentially compromised through man in the middle attacks. I.e. a hacker can go to a local coffee shop, which provides free Wi-Fi service and start inspecting traffic going through compromised edge devices.


## To solve this problem 
we can buy a certificate and configure the web server to use it.  Use HTTPS. 
**Force your web server to elevate to a secure connection, and do so whenever a user is authenticating or establishing a session.** A common way of enforcing this is to make sure that cookies are set to `secure` – that way, sessions can _only_ be established over HTTPS.

If using Apache or NGINX, we can redirect the requests to HTTPS requests, such as the following code in NGINX.

```perl

server {
  listen 80;
  rewrite ^(.*) https://$host$1 permanent;
}
```

And in Apache:

```ruby
RewriteEngine On
RewriteCond %{SERVER_PORT} !^443$
RewriteRule ^(.*)$ https://%{HTTP_HOST}/$1 [QSA,NC,R,L]
```
