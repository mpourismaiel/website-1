+++
fragment = "item"
disabled = true
date = "2017-11-04"
weight = 350
background = "light"
align = "left"

title = "Dynamic subdomain import"

icon = "fas fa-arrow-down"

pre = "*pkg.txtdirect.org/v0.1.0*"
post = "*github.com/txtdirect/txtdirect/tree/0.1.0*"
+++

* Point your chosen subdomain by CNAME to `gopkg.link.`
* Create a TXT record with the subdomain `_redirect` for your subdomain
* Use the open TXTDirect spec to set your regex to split up traffic
* Use the open TXTDirect spec to configure various paths to multiple repositories

Reusing path for version:
```text
pkg.txtdirect.org                     86000 IN CNAME   gopkg.link.
_redirect.pkg.txtdirect.org           86000 IN TXT     "v=txtv0;from=/$1;to=https://github.com/txtdirect/txtdirect/tree/{1};type=gometa-path"
```

Specific versions (enables separate repositories per version/path):
```text
pkg.txtdirect.org                     86000 IN CNAME   gopkg.link.
_redirect.pkg.txtdirect.org           86000 IN TXT     "v=txtv0;from=/$1;type=path"
_redirect.v0-1-0.pkg.txtdirect.org    86000 IN TXT     "v=txtv0;to=https://github.com/txtdirect/txtdirect/tree/v0.1.0;type=gometa"
_redirect.v0-2-0.pkg.txtdirect.org    86000 IN TXT     "v=txtv0;to=https://github.com/txtdirect/txtdirect/tree/v0.2.0;type=gometa"
```

How to use dynamic imports including the supported simplified and full regex available is available in our [documentation](/hosted/gopkg/docs)"""
