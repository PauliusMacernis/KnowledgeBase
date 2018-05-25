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
