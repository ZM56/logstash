## Create certs for Kafka connect

```shell
openssl pkcs12 -export -in client.crt -inkey client.key -out cert.p12 -caname client -passout pass:mypassword
keytool -importcert -alias CARoot -file ./root-ca.crt -keystore server.jks -storepass password
```

Create secret in k8s:
```shell
kubectl create secret generic kafka-client-cert --from-file=cert.p12 --from-file=server.jks -n logging
```
