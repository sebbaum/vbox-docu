# Get vbox
First of all download and unpack the latest release from Github:
[Download](https://github.com/ion2s-gmbh/vbox/releases/tag/v1.8.0)

```bash
unzip vbox-1.8.0.zip
# OR
tar xvfz vbox-1.8.0.tar.gz
```

Alternatively, you can clone the repo directly using Git:
```bash
git clone git@github.com:ion2s-gmbh/vbox.git
```

# Create the config file.
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
[http://10.0.0.42](http://10.0.0.42) and show the php info page.
