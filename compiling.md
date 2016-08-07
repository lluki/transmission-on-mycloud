Compile transmission
====================
This section contains some notes how one can build transmission in the WD GPL package.
* Replace /bin/sh with /bin/bash in all the xbuild.sh
* Link libiconv.so to the correct lib search path
* Tell configure to use libz

* patch libevent xbuild:
* GPL\_PREFIX=$PWD/../_xinstall/${PROJECT_NAME} cp -rvf include/event2 ${GPL\_PREFIX}/include/event2
* build libevent builden

* replace ac-local-1.14 with 1.15 in the Makefile
* CFLAGS contains too many -I directives, delete empty one (i.e change -I -I ... to -I ...) 


