## Getting started:

* clone this repo

* create a secrets folder

`mkdir -p ../minimagnus-secrets/ssh`

* generate SSH keys into that secrets folder

`ssh-keygen -t rsa -b 4096 -C "minimagnus" -f ./secrets/ssh/pi`

* copy your public key to ~pi on each node

`ssh-copy-id pi1.local`

## Bootstrap a new node:
* ansible-playbook bootstrap.yml -i inventory --limit=pi1.local

Setup all bootstrapped hosts
* ansible-playbook site.yml -i inventory
(note that --check and --diff are usually helpful)

TODO:
* testing
