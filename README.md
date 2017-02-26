# Build scripts for fuse-nfs

Each folder in the project root directory contains a shell script called mkbuild.
This script clones/updates the corresponding git repository and builds the programm/lib.

These build scripts have been tested on a devuan linux distrbution. For the linux build, libfuse-dev is required.
For the windows builds, binutils-mingw-w64-i686 and binutils-mingw-w64-x86-64 are required.
