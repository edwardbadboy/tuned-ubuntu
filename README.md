![Ubuntu-Tuned][1]

*Tuned: Daemon for monitoring and adaptive tuning of system devices.*

This is **Tuned 2** adapted for Ubuntu systems

How to use it
-------------
First, install it on your system:

    # apt-get install git git-core build-essential
    # apt-get install rpm python-decorator python-dbus python-gobject python-pyudev python-configobj
    $ git clone https://github.com/edwardbadboy/tuned-ubuntu.git
    $ sudo make install

After the installation, restart your system.

Once tuned is running (after reboot) you can easily control it using **tuned-adm** command
line utility. This tool communicates with the daemon over DBus. Any user can
list the available profiles and see which one is active. But the profiles can
be switched only by root user or by any user with physical console allocated
on the machine (X11, physical tty, but no SSH).

To see the current active profile, run:

    $ tuned-adm active

To list all available profiles, run:

    $ tuned-adm list

To switch to a different profile, run:

    # tuned-adm profile <profile-name>

And to disable all tunings, run:

    # tuned-adm off

Other options:

    # tuned-adm recommend

Recommend profile suitable for your system. Currently only static detection is
implemented - it decides according to data in /etc/system-release-cpe and
virt-what output. The rules for autodetection are defined in recommend.conf
in profile directory. They can be overriden by user by putting the
recommend.conf into /etc/tuned. The default rules recommends profiles targeted
to the best performance or balanced profile if unsure.

Your profile choice is also written into **/etc/tuned/active_profile** and this
choice is used when the daemon is restarted (e.g. with the machine reboot).


Available tunings
-----------------

Some information about the current available tunings is available via the Red Hat Documentation over here: [https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Power_Management_Guide/tuned-adm.html][2]


Authors
-------

The best way to contact the authors of the project is to use our mailing list:
**power-management@lists.fedoraproject.org**

In case you want to contact individual author, you will find the e-mail
address in every commit message in our Git repository:
[http://git.fedorahosted.org/cgit/tuned.git][3]

You can also join **#fedora-power** IRC channel on Freenode.


License
-------

Copyright (C) 2008-2012 Red Hat, Inc.

This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 2
of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.

Full text of the license is enclosed in COPYING file.


  [1]: https://spideroak.com/share/PBSW433EMVZXS43UMVWXG/78656e6f6465/srv/CDN/xenodecdn/github-assets/ubuntu-tuned-logo.png
  [2]: https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Power_Management_Guide/tuned-adm.html
  [3]: http://git.fedorahosted.org/cgit/tuned.git