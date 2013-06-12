# nginx config examples

I am learning nginx, and need a sandbox to experiment with the config file syntax and run some tests.
This is it. To use it, simply run `vagrant up`.

## conditional-blocking

This snippet achieves an equivalent effect as the following (invalid) conditional:
```
if ($suspicious_ip = 1 && ($suspicious_agent = 1 || $request_method = HEAD) {
  return 403;
}
```

Resources:

* [Nginx Blocking by User Agent | Web and IT Support Blog](http://www.itwebsupport.com/blog/nginx-blocking-by-user-agent)
* [Blocking by user agent if ip doesn't match - Ruby Forum](http://www.ruby-forum.com/topic/1829845)
* [Nginx Hardening - Some Good Security Practices - fralef.me](http://fralef.me/nginx-hardening-some-good-security-practices.html)
* [Nginx Block And Deny IP Address OR Network Subnets](http://www.cyberciti.biz/faq/linux-unix-nginx-access-control-howto/)
* [Use Nginx to server different pages depending on IP address/subnet - Server Fault](http://serverfault.com/questions/267611/use-nginx-to-server-different-pages-depending-on-ip-address-subnet)
* [Nginx how to multiple if statements - Ross Lawley](http://rosslawley.co.uk/2010/01/nginx-how-to-multiple-if-statements/)
* [Module ngx_http_geo_module](http://nginx.org/en/docs/http/ngx_http_geo_module.html)
