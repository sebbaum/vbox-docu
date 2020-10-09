# Nodejs

Nodejs is installed via NVM (Node Version Manager). This way you have the
flexibility to switch between multiple Node versions.

In `box.yml` you can define which Node version should be installed during provisioning
and which version is the default version.
```yaml
node:
  current: lts/erbium
  versions:
    - lts/erbium
    - '*' # -> latest version
```
This will install the latest LTS version of the Erbium line as well as the latest
Node version (currently: 14.13.1).
The version `lts/erbium` is set as the current version and is therefore used as the
default.
In order to define the latest installed version as current (default) version you can use the
alias `node`.
```yaml
node:
  current: node
  versions:
    - lts/erbium
    - '*' # -> latest version
```

For more details about NVM have a look at: [https://github.com/nvm-sh/nvm](https://github.com/nvm-sh/nvm)
