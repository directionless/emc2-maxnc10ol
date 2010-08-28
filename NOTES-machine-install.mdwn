1. Install Ubuntu 8.04 Server.
   Do this as minimally as possible.

   a) disk: 37gb /
            3gb swap

   b) openssh server task (only)
      reboot

2. basic machine stuff
   apt-get update
   apt-get dist-upgrade

3. Install X. Don't need gnome
   apt-get install xserver-xorg xdm ctwm xfonts-100dpi xfonts-75dpi xfonts-base
   apt-get install xterm menu
   dpkg-reconfigure xserver-xorg
   # (beware broken monitors)

4. Install EMC2
   http://www.linuxcnc.org/hardy/emc2-install.sh

4.a. You might need to tweak kernel boot order.
  reboot

5. Remove extra crud
   apt-get remove cupsys cupsys-common
   apt-get autoremove
   dpkg -l | awk '!/^ii/{print $2}' | xargs dpkg --purge

6. some random pre-reqs
   apt-get install bc gedit

7. and we need git
   wget -O- 'http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xA1715D88E1DF1F24' | apt-key add -
   echo deb http://ppa.launchpad.net/git-core/ppa/ubuntu hardy main > /etc/apt/sources.list.d/ppa-git.list
   apt-get update
   apt-get install git-core



8. Start playing with emc!

  a. latency-test
     run for a bit
     max int (1ms):    1118010
     max jitter(1ms):   121505
     max int (25us):    153355
     max jitter(25us):  129050

  b. The MaxNC 10 OL configs
     git clone http://github.com/directionless/emc2-maxnc10ol.git
