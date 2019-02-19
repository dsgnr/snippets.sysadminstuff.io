---
layout: post
title: SSL Cipher Checks
categories: ssl
permalink: /:categories/:title
---

Check what SSL ciphers are active on a web server:

{% highlight python %}
nmap --script ssl-enum-ciphers 8.8.8.8 -p 443

    Starting Nmap 6.40 ( http://nmap.org ) at 2018-05-01 15:19 UTC
    Nmap scan report for google-public-dns-a.google.com (8.8.8.8)
    Host is up (0.0025s latency).
    PORT    STATE SERVICE
    443/tcp open  https
    | ssl-enum-ciphers:
    |   TLSv1.0:
    |     ciphers:
    |       TLS_RSA_WITH_3DES_EDE_CBC_SHA - strong
    |       TLS_RSA_WITH_AES_128_CBC_SHA - strong
    |       TLS_RSA_WITH_AES_256_CBC_SHA - strong
    |     compressors:
    |       NULL
    |   TLSv1.1:
    |     ciphers:
    |       TLS_RSA_WITH_3DES_EDE_CBC_SHA - strong
    |       TLS_RSA_WITH_AES_128_CBC_SHA - strong
    |       TLS_RSA_WITH_AES_256_CBC_SHA - strong
    |     compressors:
    |       NULL
    |   TLSv1.2:
    |     ciphers:
    |       TLS_RSA_WITH_3DES_EDE_CBC_SHA - strong
    |       TLS_RSA_WITH_AES_128_CBC_SHA - strong
    |       TLS_RSA_WITH_AES_128_GCM_SHA256 - strong
    |       TLS_RSA_WITH_AES_256_CBC_SHA - strong
    |       TLS_RSA_WITH_AES_256_GCM_SHA384 - strong
    |     compressors:
    |       NULL
    |_  least strength: strong

    Nmap done: 1 IP address (1 host up) scanned in 1.36 seconds
{% endhighlight %}


{% highlight python %}

openssl ciphers 'ALL:+HIGH:!ADH:!EXP:!SSLv2:!SSLv3:!MEDIUM:!LOW:!NULL:!MD5:!DSS:!3DES:!aNULL:!PSK' -v

    ECDHE-RSA-AES256-GCM-SHA384 TLSv1.2 Kx=ECDH     Au=RSA  Enc=AESGCM(256) Mac=AEAD
    ECDHE-ECDSA-AES256-GCM-SHA384 TLSv1.2 Kx=ECDH     Au=ECDSA Enc=AESGCM(256) Mac=AEAD
    ECDHE-RSA-AES256-SHA384 TLSv1.2 Kx=ECDH     Au=RSA  Enc=AES(256)  Mac=SHA384
    ECDHE-ECDSA-AES256-SHA384 TLSv1.2 Kx=ECDH     Au=ECDSA Enc=AES(256)  Mac=SHA384
    DH-DSS-AES256-GCM-SHA384 TLSv1.2 Kx=DH/DSS   Au=DH   Enc=AESGCM(256) Mac=AEAD
    DH-RSA-AES256-GCM-SHA384 TLSv1.2 Kx=DH/RSA   Au=DH   Enc=AESGCM(256) Mac=AEAD
    DHE-RSA-AES256-GCM-SHA384 TLSv1.2 Kx=DH       Au=RSA  Enc=AESGCM(256) Mac=AEAD
    DHE-RSA-AES256-SHA256   TLSv1.2 Kx=DH       Au=RSA  Enc=AES(256)  Mac=SHA256
    DH-RSA-AES256-SHA256    TLSv1.2 Kx=DH/RSA   Au=DH   Enc=AES(256)  Mac=SHA256
    DH-DSS-AES256-SHA256    TLSv1.2 Kx=DH/DSS   Au=DH   Enc=AES(256)  Mac=SHA256
    ECDH-RSA-AES256-GCM-SHA384 TLSv1.2 Kx=ECDH/RSA Au=ECDH Enc=AESGCM(256) Mac=AEAD
    ECDH-ECDSA-AES256-GCM-SHA384 TLSv1.2 Kx=ECDH/ECDSA Au=ECDH Enc=AESGCM(256) Mac=AEAD
    ECDH-RSA-AES256-SHA384  TLSv1.2 Kx=ECDH/RSA Au=ECDH Enc=AES(256)  Mac=SHA384
    ECDH-ECDSA-AES256-SHA384 TLSv1.2 Kx=ECDH/ECDSA Au=ECDH Enc=AES(256)  Mac=SHA384
    AES256-GCM-SHA384       TLSv1.2 Kx=RSA      Au=RSA  Enc=AESGCM(256) Mac=AEAD
    AES256-SHA256           TLSv1.2 Kx=RSA      Au=RSA  Enc=AES(256)  Mac=SHA256
    ECDHE-RSA-AES128-GCM-SHA256 TLSv1.2 Kx=ECDH     Au=RSA  Enc=AESGCM(128) Mac=AEAD
    ECDHE-ECDSA-AES128-GCM-SHA256 TLSv1.2 Kx=ECDH     Au=ECDSA Enc=AESGCM(128) Mac=AEAD
    ECDHE-RSA-AES128-SHA256 TLSv1.2 Kx=ECDH     Au=RSA  Enc=AES(128)  Mac=SHA256
    ECDHE-ECDSA-AES128-SHA256 TLSv1.2 Kx=ECDH     Au=ECDSA Enc=AES(128)  Mac=SHA256
    DH-DSS-AES128-GCM-SHA256 TLSv1.2 Kx=DH/DSS   Au=DH   Enc=AESGCM(128) Mac=AEAD
    DH-RSA-AES128-GCM-SHA256 TLSv1.2 Kx=DH/RSA   Au=DH   Enc=AESGCM(128) Mac=AEAD
    DHE-RSA-AES128-GCM-SHA256 TLSv1.2 Kx=DH       Au=RSA  Enc=AESGCM(128) Mac=AEAD
    DHE-RSA-AES128-SHA256   TLSv1.2 Kx=DH       Au=RSA  Enc=AES(128)  Mac=SHA256
    DH-RSA-AES128-SHA256    TLSv1.2 Kx=DH/RSA   Au=DH   Enc=AES(128)  Mac=SHA256
    DH-DSS-AES128-SHA256    TLSv1.2 Kx=DH/DSS   Au=DH   Enc=AES(128)  Mac=SHA256
    ECDH-RSA-AES128-GCM-SHA256 TLSv1.2 Kx=ECDH/RSA Au=ECDH Enc=AESGCM(128) Mac=AEAD
    ECDH-ECDSA-AES128-GCM-SHA256 TLSv1.2 Kx=ECDH/ECDSA Au=ECDH Enc=AESGCM(128) Mac=AEAD
    ECDH-RSA-AES128-SHA256  TLSv1.2 Kx=ECDH/RSA Au=ECDH Enc=AES(128)  Mac=SHA256
    ECDH-ECDSA-AES128-SHA256 TLSv1.2 Kx=ECDH/ECDSA Au=ECDH Enc=AES(128)  Mac=SHA256
    AES128-GCM-SHA256       TLSv1.2 Kx=RSA      Au=RSA  Enc=AESGCM(128) Mac=AEAD
    AES128-SHA256           TLSv1.2 Kx=RSA      Au=RSA  Enc=AES(128)  Mac=SHA256
{% endhighlight %}

