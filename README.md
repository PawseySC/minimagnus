Usage:
* copy your public key to ~pi on each node
`ssh-copy-id pi1.local`

* On prime node, git clone pibrot
`git clone https://github.com/TinyTitan/PiBrot.git`

* On prime node, git clone SPH
`git clone https://github.com/TinyTitan/SPH.git

* ansible-playbook site.yml -i inventory
(note that --check and --diff are usually helpful)

TODO:
* various makes
