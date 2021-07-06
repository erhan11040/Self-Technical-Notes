OPEN SSL NOTES

openssl pkcs12 -inkey private.pem -in cert.pem -export -out cert-test.pfx -password pass:xxxxx
openssl pkcs12 -in cert-test.pfx -out cert-test.cer -nodes

openssl pkcs12 -inkey private-dev.pem -in cert-dev.pem -export -out cert-dev.pfx -password pass:xxxxx
openssl pkcs12 -in cert-dev.pfx -out cert-dev.cer -nodes

first part of the first one
all of second one

openssl pkcs12 -inkey tls.key -in tls.crt -export -out cert-prod.pfx -password pass:xxxxx
openssl pkcs12 -in cert-prod.pfx -out cert-prod.cer -nodes