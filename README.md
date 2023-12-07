# client-ssl-cert

```
#!/bin/bash

name=${name:-cert}
openssl genrsa -out "$name.key" 4096
openssl req -new -key "$name.key" -out "$name.csr"
openssl x509 -req -days "${days:-356}" -in "$name.csr" -signkey "$name.key" -out "$name.crt"
openssl pkcs12 -export [-legacy](https://stackoverflow.com/a/73512646) -inkey "$name.key" -in "$name.crt" -out "$name.pfx"
```
