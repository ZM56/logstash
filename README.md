## Create certs for Kafka connect

```shell
openssl pkcs12 -export -in client.crt -inkey client.key -out cert.p12 -caname client -passout pass:mypassword
keytool -importcert -alias CARoot -file ./root-ca.crt -keystore server.jks -storepass password
```
