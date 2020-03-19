Usage:
* copy your public key to ~pi on each node
`ssh-copy-id pi1.local`

* clone this repo

Bootstrap a new node:
* ansible-playbook bootstrap.yml -i inventory --limit=pi1.local

Setup all bootstrapped hosts
* ansible-playbook site.yml -i inventory
(note that --check and --diff are usually helpful)

TODO:
* testing
