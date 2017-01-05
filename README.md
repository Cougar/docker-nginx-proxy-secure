Secure [nginx-proxy][1]. By default all access is denied. Access can be allowed globally in `default_access` or per virtual host in `{VIRTUAL_HOST}_access` file in '/etc/nginx/access.d' directory.

#### Per-VIRTUAL_HOST access configuration

To make any virtual host accessible, add `{VIRTUAL_HOST}_access` file under `/etc/nginx/access.d/`. Contents of this file will be added to the "location" block in `VIRTUAL_HOST`.

For example

```Nginx
deny  192.168.1.1;
allow 192.168.1.0/24;
allow 10.1.1.0/16;
allow 2001:0db8::/32;
deny  all;
```

#### Per-VIRTUAL_HOST access default configuration

If you want most of your virtual hosts to use a default single access policy, add it to the `/etc/nginx/access.d/default_access` file. This file will be used on any virtual host which does not have a `/etc/nginx/access.d/{VIRTUAL_HOST}_access` file.

If `/etc/nginx/access.d/default_access` does not exists then all access is denied by `deny all;` rule.

  [1]: https://hub.docker.com/r/jwilder/nginx-proxy/
