# Get vbox
Basically, there are four ways of using the Vbox in your own webproject:
1. Download and extract the Vbox code. No Github account in needed.
1. Use the Template-Repo.
1. Clone the Vbox repo and start with a fresh `git init`.
1. Use the Vbox as a git submodule.

For simplicity we use the first option here.
So start by downloading and unpacking the latest release from Github:
[Download](https://github.com/ion2s-gmbh/vbox/releases)

```bash
unzip vbox-1.17.0.zip

# OR

tar xvfz vbox-1.17.0.tar.gz
```

Alternatively, you can clone the repo directly using Git:
```bash
git clone https://github.com/ion2s-gmbh/vbox.git
```

# Create the config file
Make a copy of the sample config file and use it as the starting ground for your
box's setup.

```bash
cp configure/box.sample.yml box.yml
```

!!! important "No more config needed"
    At this point, you don't need to change any configuration.
    However, you'll find more detailed information about the configuration in the [configuration](configuration.md) section.

# Start the box
Finally, all you have to do is running `vagrant up` and grep yourself a cup of
tea or coffee.

Once the provisioning is finished, your preferred browser should open
[http://10.0.0.101](http://10.0.0.101) and show the php info page.
