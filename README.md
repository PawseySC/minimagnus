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

## Connecting a controller
Currently the recommended controller is the Xbox 360 Wireless Controller paired with an official
"Xbox 360 Controller for Windows" USB dongle, which is usually sold as a kit. Unfortunately these
are no longer being made and they are getting very hard and expensive to find.

Any controller that you can map to keyboard keys + mouse control could be made to work.

Check out SPH/controller_1.cnf to see how the Xbox controller works.

## Getting the SPH demo working
The Ansible run will have placed most of the resources needed for the SPH demo in the appropriate places.

You will need to use the included makefiles to build the SPH demo and push it to the compute nodes.

It's simpler than it sounds.

* On your prime node, change to the /home/pi/SPH directory

`cd /home/pi/SPH`

* Run `make` to compile the demo

`make`

* Now run `make run` to push it out and try it.

`make run`

Check that everything seems to work. To exit the demo, hit the "Back" button,
then move the "leaf" cursor over the Terminal image and press the "A" button.

Now that the SPH demo has been built and pushed, it can be run by the Kiosk script later.

## Getting the PiBrot (Mandelbrot) demo working
As with the SPH demo, the Ansible run will have already placed most resources needed for PiBrot.

You will need to use the included makefiles to build the PiBrot demo and push it to the compute nodes.

* On your prime node, change to the /home/pi/PiBrot directory

`cd /home/pi/PiBrot`

* Run `make` to compile the demo

`make`

* Run `make run` to push it out and try it.

`make run`

To start the demo, use the left thumbstick on your controller to move the "leaf" cursor over the
Start button, then press the A button. To exit the demo, hit the "Back" button,
then move the cursor over the Terminal image and press the "A" button.

Now that the PiBrot demo has been built and pushed, it can be run by the Kiosk script later.

## Putting it all together - the Kiosk script
We have included a "kiosk" script which currently lives at /home/pi/startsph. It's a simple bash
script that uses exit codes to switch between the two included TinyTitan demos.

Also included is a custom rc.local file which sets up keymapping from the Xbox 360 Controller's
buttons and controls to the appropriate keyboard and mouse inputs. If you press the "Guide" button
(the Xbox button in the middle of the controller), the Kiosk script is automatically started.

By default, the Kiosk script will boot into the SPH demo, but you can use the menu triggered by
the "Back" button to switch between demos. Just move the cursor as before over what you want, then hit A.

Selecting the "Terminal" demo will simply exit the Kiosk script and leave you on the Raspbian desktop.

## TODO
* More documentation

* Rename startsph to startkiosk
