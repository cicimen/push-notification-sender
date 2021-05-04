# push-notification-sender

## Apple

https://developer.apple.com/forums/thread/88332

### Convert p12 to pem

Bu sertifika https://github.com/relateddigital/euromessage-ios projesine ait. Şifresi 1660. 

Bundle Identifier : com.relateddigital.EuromsgExample

```
openssl pkcs12 -in Certificates.p12 -out pushcert.pem -nodes -clcerts
```

Yeni yüklediğim uygulamanın token'ı ile "6C5C596BC990F6A71FCAEEE49F4DE8088B7A91B68A9A78CC8D16793D93589A13"

```
curl -v -d '{"aps":{"alert":"Deneme","badge":1}}' -H "apns-topic:com.relateddigital.EuromsgExample" --http2 --cert pushcert.pem https://api.sandbox.push.apple.com/3/device/6C5C596BC990F6A71FCAEEE49F4DE8088B7A91B68A9A78CC8D16793D93589A13
```

Eğer canlı uygulamaya push atacaksan aşağıdaki endpoint'i kullan.

`https://api.development.push.apple.com/3/device`

Uygulama yüklü iken dönen sonuç aşağıdaki şekilde:

```
*   Trying 17.188.138.71...
* TCP_NODELAY set
* Connected to api.sandbox.push.apple.com (17.188.138.71) port 443 (#0)
* ALPN, offering h2
* ALPN, offering http/1.1
* successfully set certificate verify locations:
*   CAfile: /etc/ssl/cert.pem
  CApath: none
* TLSv1.2 (OUT), TLS handshake, Client hello (1):
* TLSv1.2 (IN), TLS handshake, Server hello (2):
* TLSv1.2 (IN), TLS handshake, Certificate (11):
* TLSv1.2 (IN), TLS handshake, Server key exchange (12):
* TLSv1.2 (IN), TLS handshake, Request CERT (13):
* TLSv1.2 (IN), TLS handshake, Server finished (14):
* TLSv1.2 (OUT), TLS handshake, Certificate (11):
* TLSv1.2 (OUT), TLS handshake, Client key exchange (16):
* TLSv1.2 (OUT), TLS handshake, CERT verify (15):
* TLSv1.2 (OUT), TLS change cipher, Change cipher spec (1):
* TLSv1.2 (OUT), TLS handshake, Finished (20):
* TLSv1.2 (IN), TLS change cipher, Change cipher spec (1):
* TLSv1.2 (IN), TLS handshake, Finished (20):
* SSL connection using TLSv1.2 / ECDHE-RSA-AES256-GCM-SHA384
* ALPN, server accepted to use h2
* Server certificate:
*  subject: CN=api.development.push.apple.com; OU=management:idms.group.533599; O=Apple Inc.; ST=California; C=US
*  start date: Feb  8 21:41:22 2021 GMT
*  expire date: Mar 10 21:41:22 2022 GMT
*  subjectAltName: host "api.sandbox.push.apple.com" matched cert's "api.sandbox.push.apple.com"
*  issuer: CN=Apple Public Server RSA CA 12 - G1; O=Apple Inc.; ST=California; C=US
*  SSL certificate verify ok.
* Using HTTP2, server supports multi-use
* Connection state changed (HTTP/2 confirmed)
* Copying HTTP/2 data in stream buffer to connection buffer after upgrade: len=0
* Using Stream ID: 1 (easy handle 0x7fed0380d600)
> POST /3/device/6C5C596BC990F6A71FCAEEE49F4DE8088B7A91B68A9A78CC8D16793D93589A13 HTTP/2
> Host: api.sandbox.push.apple.com
> User-Agent: curl/7.64.1
> Accept: */*
> apns-topic:com.relateddigital.EuromsgExample
> Content-Length: 36
> Content-Type: application/x-www-form-urlencoded
> 
* Connection state changed (MAX_CONCURRENT_STREAMS == 1000)!
* We are completely uploaded and fine
< HTTP/2 200 
< apns-id: D917CA4B-AE9F-4549-45F7-126FB07D027D
< 
* Connection #0 to host api.sandbox.push.apple.com left intact
* Closing connection 0
```

