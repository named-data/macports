Using NDN MacPorts repo
=======================

Mac users have an opportunity to install ccnx and enjoy seamless auto-configuration using MacPorts.

The first thing that is necessary is to install MacPorts on the system, if you don't have them yet. To do so, please go to MacPorts site (http://www.macports.org/), download and install the package.

Second, because ccnx is not yet part of the standard ports, you need to do minor configuration of MacPorts. In particular, you will need to modify list of source URLs for MacrPorts. If your MacPorts are installed in /opt/local, add the following line at the end of `/opt/local/etc/macports/sources.conf` before the default port repository:

        rsync://macports.named-data.net/macports/

After this step, you can use "`sudo port selfupdate`" to fetch updated port definitions.

The following command will install ccnx using MacPorts

        sudo port install ccnx

Very last piece is to run "`sudo port load ccnx`", which will start ccnx, make it start on startup, and makes auto-configuration scripts to be rerun every time there is a change in connectivity. 

Public key management
---------------------

Please refer to this instructions http://github.com/named-data/ndn-testbed-key-suite/wiki/Key-publishing-for-users to extract public key, install a certified public key (.pubcert file) received from your site's operator, and sign public key of unprivileged user that runs ccnd and ccnd auto-configuration process with MacPorts.

Prerequisites
-------------

### XCode

You have to have XCode installed on your machine.  For latest versions of OSX (Lion or Mountain Lion) you can install it from AppStore for free, for older versions you have to go to developer.apple.com and download old version of XCode that is appropriate for your system.

Upgrading ccnx
-----------------

If you previously installed ccnx, you may need to upgrade to the latest version available.  To do so, the following commands may be used

       sudo port selfupdate
       sudo port unload ccnx
       sudo port upgrade ccnx
       sudo port load ccnx

Other recommended tools
-----------------------------

#### Chronos: multi-party chat application

* [Get binaries or sources on Chronos homepage.](http://irl.cs.ucla.edu/~zhenkai/chronos.html)

There are a couple of other NDN tools that are available in MacPorts and are recommended to be installed:

#### ccnping 

        sudo port install ccnping

You can try it after to ping some testbed one:

        ccnping /ndn/ucla.edu

#### ccnx-trace

        sudo port install ccnx-trace
        sudo port load ccnx-trace

This will install traceroute tool for NDN and will start daemon that is necessary for it.  For more information refer to [ccnx-trace website](http://code.google.com/p/ccnx-trace/).

#### python bindings

        sudo port install py27-pyccn

#### ndnvideo

Small warning. `ndnvideo` has a substantial number of dependencies, which may result in a prolonged installation time, especially for Mountain Lion users where each dependency need to be compiled from the source.

        sudo port install py27-ndnvideo
        ndnplay /ndn/ucla.edu/apps/video_remap
        ndnplay /ndn/arizona.edu/apps/video
        ndnplay /ndn/uiuc.edu/apps/video

Other available tools
-----------------------

#### repo

     sudo port install ccnx-repo
     sudo port load ccnx-repo

This will start (and restart if necessary) ccn repo.

