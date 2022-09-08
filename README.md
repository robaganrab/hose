# Home Server

Home server project for Raspberry and x64 architecture.

## Goals of the project

Create a home server on a Raspberry Pi, while also
adding an x64 machine's (eg. laptop) resources when
it is available locally.

### Outcome wish list

- Learning about
  - Server management
  - Containerization
  - CI/CD
  - Networking
- Self upgrading system
- Home Assistant is hosted
- Media server is hosted

### Technical requirements wish list

- k8s based platform (due to RPi, k3s is needed)
- Accessible from the internet to send in data
  - Let's encrypt secured TLS/HTTPS
- Secured LAN communication between nodes
- Easy to deploy/recreate, but no need for full automation
- Declarative service description
- Test driven development/deployment/roll back, health checks
- Single sign on to secure all exposed services

## Resources

### erebe/personal-server

[https://github.com/erebe/personal-server][erebe/personal-server]

Ideas to use from here: GPG and SOPS secured secret
management, Let's Encrypt, maybe more.

[healthchecks.io]: https://healthchecks.io/
[k9s]: https://k9scli.io/
[erebe/personal-server]: https://github.com/erebe/personal-server
