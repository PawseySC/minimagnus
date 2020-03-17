Usage:
* copy your public key to ~pi on each node
`ssh-copy-id pi1.local`

* install git

* On prime node, git clone pibrot
`git clone https://github.com/TinyTitan/PiBrot.git`

* On prime node, git clone SPH
`git clone https://github.com/TinyTitan/SPH.git

* clone this repo

* ansible-playbook site.yml -i inventory
(note that --check and --diff are usually helpful)

TODO:
* testing
