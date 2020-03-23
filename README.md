## Getting started:

* clone this repo

* create a secrets folder

`mkdir -p ../minimagnus-secrets/ssh`

* generate SSH keys into that secrets folder

`ssh-keygen -t rsa -b 4096 -C "minimagnus" -f ./secrets/ssh/pi`

* copy your public key to ~pi on each node

`ssh-copy-id pi1.local`

* customise to your needs (edit hosts file, inventory etc)

* use Ansible to build the cluster

`ansible-playbook site.yml -i inventory`

(Note that --check and --diff are usually helpful)

## TODO
* More documentation

* Rename startsph to startkiosk
