# Ingress

## The problem with NodePort
NodePort works but it's not scalable. Every app needs its own random port and users
have to know the port number to reach anything. That's not how the real internet
works.

## What Ingress does
Ingress routes traffic based on domain name or URL path through a single entry point.
One entry point, multiple apps, and clean URLs.

## Ingress resource vs Ingress Controller
Two different things that confuse me:

- **Ingress resource** its the YAML rulebook. Does nothing on its own.
- **Ingress Controller** is the software that reads and enforces those rules.
  Has to be installed separately, Kubernetes doesn't ship with one.

`ingressClassName: nginx` in the YAML tells Kubernetes which controller should
enforce the rules.

## Local DNS trick
nginx.local isn't a real domain. I had to manually configure my pc what it
resolves to by editing the hosts file at:
C:\Windows\System32\drivers\etc\hosts

Without this the browser throws a DNS error, it has no idea where nginx.local points.