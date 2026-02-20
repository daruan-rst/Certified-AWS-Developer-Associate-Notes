# Elastic Load Balancer SSL Certificates

## SSL/TLS - Basics

- An SSL Certificate allows traffic between your client and a load balancer to be encrypted in transit (in-flight encryptation)

- SSL refers to Secure Sockets Layer, used to encrypt connections
- TLS refers to Transport Layer Security, which is a newer version
-  Nowadays, TLS certificates are mainly used, but people still call them as SSL

- Public SSL certificates are issued by Certificate Authorities (CA)
    - Examples: Comodo, Symantec, GoDaddy, GlobalSign, Digicert, Letsencrypt, etc ...

- SSL certificates have an expiration date (which is set by you) and must be renewed

## Load Bancer - SSL certificates

1. Users connect from an HTTPS - and the S comes from SSL certificates - over the public internet to a Load Balancer
2. Internally, the Load Balancer does a SSL termination
3. In the backend, the Load Balancer comunicates with any EC2 instance via HTTP - which is not encrypted - but the trafic goes over a VPC, which is private.

- The Load Balancer uses an X.509 certificate (SSL/TLS server certificate)
- You can manage certificates using ACM (AWSN Certificate Manager)
- You can create or upload your own certificates alternatively
- When setting an HTTPS listener:
     - You must specify a default certificate
     - You can add an optional list of certs to support multiple domains
     - Clients can use SNI (Server Name Indication) to specify the hostname they reach
     - Ability to specify a security policy to support older versions of SSL/TLS (legacy clients)

## SSL - Server Name Indication

- SNI solves the problem of loading multiple SSL certificates onto one web server (to serve multple websites)
- It's a newer protocol and requires the client to indicate the hostname of the target server in the initial SSL handshake
- The server will then find the correct certificate, or return the default one

Note:
- Only works for ALB & NLB (newer generation), Cloudfront
- Does not work for CLB (older gen)


