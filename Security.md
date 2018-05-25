### Security
- What is the difference between identification and authentication?
<a href="#" title="
">⌘</a>
  
- What is the difference between authorization and authentication?
<a href="#" title="
">⌘</a>
  
- What is the difference between authorization and ACL?
<a href="#" title="
">⌘</a>
  
- What is challenge-response authentication mechanism (CRAM)?
<a href="#" title="
">⌘</a>
  
- What is Security Support Provider Interface (SSPI)?
<a href="#" title="
">⌘</a>
  
- What is Trusted Authentication?
<a href="#" title="
">⌘</a>

- What is Bearer Token?
<a href="#" title="
">⌘</a>

- What is Basic Auth?
<a href="#" title="
">⌘</a>

- What is Digest Auth?
<a href="#" title="
">⌘</a>

- What is OAuth?
<a href="#" title="
">⌘</a>

- What is Hawk Authentication?
<a href="#" title="
">⌘</a>

- What is AWS Signature?
<a href="#" title="
">⌘</a>

- What is NTLM Authentication?
<a href="#" title="
">⌘</a>

- What are differences between OAuth 1.0 and OAuth 2.0?
<a href="#" title="
">⌘</a>
  
- What is Kerberos (protocol) about?
<a href="#" title="
">⌘</a>

- Explain what Transport Layer Security (TLS) is and how it is being used.
<a href="#" title="
">⌘</a>

- Explain what Secure Sockets Layer (SSL) is and how it is being used.
<a href="#" title="
">⌘</a>

- Explain what OpenSSL is and how it is being used.
<a href="#" title="
">⌘</a>

- Explain what Diffie–Hellman key exchange is and how it is being used.
<a href="#" title="
">⌘</a>

- What is the difference between 'Public key' and 'Public key certificate'? Explain dow are they being used.
<a href="#" title="
">⌘</a>

- (HTTP) Do I need to authenticate by username and password before I can authenticate by using access token?
<a href="#" title="
">⌘</a>

- **What is .crt and .key files and how to generate them?**  
These are the public (.crt) and private (.key) parts of an SSL certificate.  
The following will generate:  
`openssl genrsa 1024 > host.key`  
`chmod 400 host.key`  
`openssl req -new -x509 -nodes -sha1 -days 365 -key host.key -out host.cert`  
Note that with self-signed certificates your browser will warn you that the certificate is not "trusted" because it hasn't been signed by a certification authority that is in the trust list of your browser.  
From there onwards you can either generate your own chain of trust by making your CA or buy a certificate from a company like Verisign or Thawte.  
Read more:  
https://serverfault.com/questions/224122/what-is-crt-and-key-files-and-how-to-generate-them  

- **What is a Pem file and how does it differ from other OpenSSL Generated Key File Formats?**  
SSL has been around for long enough you'd think that there would be agreed upon container formats. And you're right, there are. Too many standards as it happens. So this is what I know, and I'm sure others will chime in.  
  - **.csr** This is a Certificate Signing Request. Some applications can generate these for submission to certificate-authorities. The actual format is PKCS10 which is defined in [RFC 2986](https://www.rfc-editor.org/info/rfc2986). It includes some/all of the key details of the requested certificate such as subject, organization, state, whatnot, as well as the public key of the certificate to get signed. These get signed by the CA and a certificate is returned. The returned certificate is the public certificate (which includes the public key but not the private key), which itself can be in a couple of formats.
  - **.pem** Defined in RFC's [1421](https://www.rfc-editor.org/info/rfc1421) through [1424](https://www.rfc-editor.org/info/rfc1424), this is a container format that may include just the public certificate (such as with Apache installs, and CA certificate files /etc/ssl/certs), or may include an entire certificate chain including public key, private key, and root certificates. Confusingly, it may also encode a CSR (e.g. as used [here](https://jamielinux.com/docs/openssl-certificate-authority/create-the-intermediate-pair.html)) as the PKCS10 format can be translated into PEM. The name is from [Privacy Enhanced Mail (PEM)](https://en.wikipedia.org/wiki/Privacy-enhanced_Electronic_Mail), a failed method for secure email but the container format it used lives on, and is a base64 translation of the x509 ASN.1 keys.
  - **.key** This is a PEM formatted file containing just the private-key of a specific certificate and is merely a conventional name and not a standardized one. In Apache installs, this frequently resides in `/etc/ssl/private`. The rights on these files are very important, and some programs will refuse to load these certificates if they are set wrong.
  - **.pkcs12** .pfx .p12 Originally defined by RSA in the [Public-Key Cryptography Standards (abbreviated PKCS)](https://en.wikipedia.org/wiki/PKCS), the "12" variant was originally enhanced by Microsoft, and later submitted as [RFC 7292](https://www.rfc-editor.org/info/rfc7292). This is a passworded container format that contains both public and private certificate pairs. Unlike .pem files, this container is fully encrypted. Openssl can turn this into a .pem file with both public and private keys: `openssl pkcs12 -in file-to-convert.p12 -out converted-file.pem -nodes`

  A few other formats that show up from time to time:  
  - **.der** A way to encode ASN.1 syntax in binary, a .pem file is just a Base64 encoded .der file. OpenSSL can convert these to .pem (`openssl x509 -inform der -in to-convert.der -out converted.pem`). Windows sees these as Certificate files. By default, Windows will export certificates as .DER formatted files with a different extension. Like...
  - **.cert** **.cer** **.crt** A .pem (or rarely .der) formatted file with a different extension, one that is recognized by Windows Explorer as a certificate, which .pem is not.
  - **.p7b** .keystore Defined in [RFC 2315](https://www.rfc-editor.org/info/rfc2315) as PKCS number 7, this is a format used by Windows for certificate interchange. Java understands these natively, and often uses .keystore as an extension instead. Unlike .pem style certificates, this format has a defined way to include certification-path certificates.
  - **.crl** A certificate revocation list. Certificate Authorities produce these as a way to de-authorize certificates before expiration. You can sometimes download them from CA websites.

  In summary, there are four different ways to present certificates and their components:  

  - **PEM** Governed by RFCs, it's used preferentially by open-source software. It can have a variety of extensions (.pem, .key, .cer, .cert, more)
  - **PKCS7** An open standard used by Java and supported by Windows. Does not contain private key material.
  - **PKCS12** A Microsoft private standard that was later defined in an RFC that provides enhanced security versus the plain-text PEM format. This can contain private key material. It's used preferentially by Windows systems, and can be freely converted to PEM format through use of openssl.
  - **DER** The parent format of PEM. It's useful to think of it as a binary version of the base64-encoded PEM file. Not routinely used by much outside of Windows.

