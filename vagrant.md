## Start
Create a directory for your VM. It will have a `data` and `box` directory. Subsequently initialize the box.

```bash
mkdir box data
cd box
vagrant init ubuntu/xenial64
```

This creates `box/Vagrantfile`

## Config Vagrantfile
[...]


## Start and join the VM

```bash
vagrant up --provider virtualbox
vagrant ssh
```

This will ssh to our VM

## Config Startup Script
Outside ssh, we can create files in `../data` and they'll show up in `/vagrant_data` inside the VM. For example,

```bash
cat > ../data/setup.sh <<EOF
#!/bin/bash
sudo apt-get update
EOF
```

## Snapshots and Tests
If you want to test something you can quickly run

```bash
vagrant snapshot push
```

Then you can proceed with the test. For example,
```bash
vagrant ssh
sudo su
chmod a+rwx /vagrant_data/setup.sh
/vagrant_data/setup.sh
# analyze results
exit
logout
```

To return to the previous state, run

```bash
vagrant snapshot pop
```
