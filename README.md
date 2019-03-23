# LightDM-service-check-control
A Light Display Manager (service) check and control script for Debian based Linux distributions (like Raspbian, not sure if it will run
on any other Linux distributions, this is script is tested on Raspbian only)

# What does it do?
Well, it checks if the lightdm service (often used by X server to control if the X server is up or not (also means if the desktop 
is running or not in Linux or *nix)) is running or not, if it's up then just stop the service and vice versa

# How does it work?
The progra... No, I mean the "script" will check for a process called "lightdm", if it's running that means the "lightdm" service
is running and vice versa, if the process is not runnning, the script will think that the service isn't runnning.
It will use the "service" command to control the service.

# How do I install it?
Emmm... I don't know if it should be called simple or not but here we go:

1. Login to your shell (and make sure the user that you use can use <i>sudo</i> command)
2. Download the "desktop" file from my repository <br>
<i>you can achieve it by using the following command:</i>
<pre>wget https://raw.githubusercontent.com/thebuster0/LightDM-service-check-control/master/desktop</pre>
3. Change the file permission
<pre>chmod 777 desktop</pre>
<i>Note: you can use whatever permission you want, but make sure it has the "Execute" permission, if not, the program will
not run or cannot be recognized</i>

4. Move it to <i>/bin/</i>
<pre>sudo mv desktop /bin/</pre>
5. Done

# How to use it? 
By default, the script should be runned <b>without any parameters</b> or it will return an "Unknown parameter error".
<pre>desktop</pre>
Bu running the script, the script will check if the service "lightdm" is running (or not), if it finds out that the service
is running, it will stop it, if it isn't running, it will start the service.

The program should output something like this:
<pre>pervertAdministrator@qt0-ayumi:~ $ desktop
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ===
Authentication is required to start 'lightdm.service'.
Multiple identities can be used for authentication:
 1.  ,,, (pervertAdministrator)
 2.  root
Choose identity to authenticate as (1-2): 1
Password:
==== AUTHENTICATION COMPLETE ===
Light Display Manager is now running, desktop/VNC is available</pre>
or
if you run it with sudo or using the <i>root</i> account it should output something like this
<pre>Light Display Manager is now running, desktop/VNC is available</pre>

another possible output is

<i>without using sudo, runned as a normal user</i>
<pre>pervertAdministrator@qt0-ayumi:~ $ desktop
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ===
Authentication is required to stop 'lightdm.service'.
Multiple identities can be used for authentication:
 1.  ,,, (pervertAdministrator)
 2.  root
Choose identity to authenticate as (1-2): 1
Password:
==== AUTHENTICATION COMPLETE ===
Light Display Manager is now stopped, desktop/VNC is unavailable</pre>
or, using sudo or root:
<pre>Light Display Manager is now stopped, desktop/VNC is unavailable</pre>

# Using this script with the -s parameter
When using the "-s" parameter, the program will just output the current service status and exit.
It won't need root permission (I think...). The following output will be the same if you use the root permission or not.
<pre>pervertAdministrator@qt0-ayumi:~ $ desktop -s
Light Display Manager is now stopped, desktop/VNC is unavailable
</pre>

# Are there help information inside the script?
Yes, there is a help guide built into the script.
To access it you can use 3 different commands:
<pre>desktop --help</pre>
<pre>desktop -h</pre>
<pre>desktop -?</pre>

It will print the parameters and it will exit directly
<pre>(No parameters): Check if the Light Display Manager service is running or not, if the service is running, stop the service (and print the status) and vice versa
-s: Print the status of the service Light Display Manager and exit
--help: Display this info/help and exit
-h: Display this info/help and exit
-?: Display this info/help and exit</pre>

But you cannot combine "-h" with "--help" or "-?" or anything else like "desktop -h --help", it will result an 
"Unknown parameter error".

Same thing with "desktop -s -h", you cannot combine the "-s" parameter (also known as a "status" parameter) with any help
parameter.

# License?
See the LICENSE file. This repository is under the public domain, you can do whatever you want.

<hr>

# Thank you for reading the whole README.md
![Kafuu Chino](/README.md.Resource/68073616.jpg)
Thank you for reading this, have a good day.
