## Getting started:
* Follow the MiniMagnus Build Guide to prepare the nodes

* Clone this repository to somewhere handy. We use a "management" laptop.

* Create a keypair for controlling the nodes
`ssh-keygen -t rsa -b 4096 -C "minimgmt"`

* Copy the newly generated public key to each node
```
ssh-copy-id pi@pi1.local
ssh-copy-id pi@pi2.local
ssh-copy-id pi@pi3.local
# rinse and repeat for the rest of your nodes
```

* Enter the repository directory
`cd minimagnus`

* Create a secrets folder
`mkdir -p ../minimagnus-secrets/ssh`

* Generate SSH keys into that secrets folder
`ssh-keygen -t rsa -b 4096 -C "minimagnus" -f ./secrets/ssh/pi`

* Edit the inventory file so it lists all of your nodes by name under the [compute] section.
`nano inventory`

* Edit the MPI hostsfile so it lists all of your nodes by IP address.
`nano mpi/mpihostsfile.j2`

* Edit the system hostsfile so it lists all your nodes and corresponding IP addresses.
`nano hosts/hosts.j2`

* Perform an Ansible run to build the cluster
`ansible-playbook site.yml -i inventory`

## Configuring a controller
MiniMagnus is based on the TinyTitan project, which originally used an "Xbox 360 Wireless Controller for Windows" kit. 

Unfortunately, it's become very hard to find those kits, and there are plenty of non-genuine kits floating around.

If you have a genuine kit and want to use it, edit rc.local.j2 and enable the Xbox 360 controller block.

The default controller block uses a Mayflash MAGIC-NS adapter running in Xbox (xinput) mode, paired with an appropriate gamepad (we recommend the Sony PlayStation 4 Dualshock 4).

If you switch controller types, you'll need to re-run the Ansible playbook.

Once you've picked your controller type, return to the Build Guide.

## TODO
* Improve documentation
* Rename startsph to startkiosk

## Neat tricks
To shut down the whole cluster:
`ansible compute -m shell -a "shutdown -h now" -i inventory --become`

To kill a simulation:
`pi@pi1:~ $ ~/killdemos.sh`
