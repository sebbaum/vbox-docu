# Configuration

The main configuration file that determines the capabilities of your vbox is
`vbox.yml`. This file can be placed in different locations. The Vagrantfile
gives precedence to the locations.

1. Outside of the vbox folder. This is useful if the vbox is integrated into an
other project.
1. Inside of the vbox itself. This is useful if the vbox is the new base of your
project and your source code is located inside of `/src`.
1. Inside the `configuration` folder of vbox where the `box.example.yml` is
placed, too. This is useful for developing the vbox itself.

## File structure
```bash
.
├── box.yml               # <-- 2. precedence
├── configure
│   ├── box.sample.yml
│   └── box.yml           # <-- 3. precedence
├── provisioning
│   ├── apache.sh
│   ├── composer.sh
│   ├── configs
│   ├── createSSLCert.sh
│   ├── docker-compose.sh
│   ├── docker.sh
│   ├── frameworks.sh
│   ├── loadNvm.sh
│   ├── memcached.sh
│   ├── mysql.sh
│   ├── nginx.sh
│   ├── nvm.sh
│   ├── packages.sh
│   ├── php.sh
│   ├── redis.sh
│   ├── scripts
│   ├── templates
│   └── welcome.sh
├── README.md
├── src
│   ├── application
│   └── index.php
└── Vagrantfile
```
