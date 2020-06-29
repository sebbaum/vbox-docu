# Docker
Docker and docker-compose can be installed in your box by enabling it in the
`box.yml` file:

```yml
provision:
  [...]
  docker: true
  [...]
```

This will install Docker CE (Community Edition) in your vagrant box. By using
Docker in your Vbox you can, for example, extend the box easily with other
required software.

!!! note "Info"
    The vagrant user is added to the docker group, so you can use docker
    commands without `sudo`.

## Additional OS packages
If Docker and docker-compose are provisioned, the following additional OS
packages will be installed:

* apt-transport-https
* ca-certificates
* curl
* gnupg-agent
* software-properties-common
