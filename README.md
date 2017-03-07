# Build scripts for fuse-nfs

This reposiory contains build scripts for https://github.com/sahlberg/fuse-nfs 

## How to use these build scripts

Each folder in the project root directory contains a shell script called `mkbuild`.
This script clones/pulls the corresponding git repository and builds the programm/lib.
Each `mkbuild` script will create the following directories:
 * `src`: The source/cloned repo
 * `build`: The source is built in this folder
 * `out`: The resulting binaries

The commit and repo url using which `fuse-nfs` is built when using this build scripts
can be changed using the environment variables `{LIBNFS,FUSENFS,DOKANY}_{URL,CHECKOUT}`
These build scripts have been tested on a devuan linux distrbution. The following
packages are required to build `fuse-nfs` using the provided build scripts:
`gcc mingw-w64 git libfuse-dev automake libtool make cmake`

If you just want to build `fuse-nfs`, use the script `/fuse-nfs/mkbuild`. 

The script `/mkbuild` (,the one in the project root directory), tries to build `fuse-nfs`
using a lot of different repo versions, which ones is specified in `/fuse-nfs/.target`,
and uploads these builds as github releases to https://github.com/Daniel-Abrecht/fuse-nfs-crossbuild-scripts/releases.
The releses in this repo are updated each hour if necessary.


## How to install a release in Windows

The first step is to choose a release. The releases are named `repo1=ref1 repo2=ref2 ...`. If `ref` is `master`, the latest commit has been used for the release. Therefore, the newest release is always `libnfs=master fuse-nfs=master dokany=master`. However, this may not be the most stable release. If you want the newest stable release, choose the one with the most and highest version numbers.

The next step is to download the correct zip archive:
 * x86_64.zip              => linux amd64
 * x86_64-w64-mingw32.zip  => Windows 64bit
 * i686-w64-mingw32.zip    => Windows 32bit

Then download & install the correct dokany driver from https://github.com/dokan-dev/dokany/releases
Usually, the latest release will work just fine. If it doesn't try to use the version matching
the one specified in the release of this repo.

Now, just unzip the downloaded folder. I recommand renaming the folder fuse-nfs and moving it to `C:\Program Files\`.
You can now use fuse-nfs by opening a CMD Window and navigating into the unzipped folder, or if it is too inconvinient
to switch into the folder, you can just add the folder to the system path. You can now type `fuse-nfs.exe -h` to display all available options. To mount a network share, the command could look like this: `fuse-nfs.exe -n nfs://share-name-or-ip/your-export -m R`. This would mount the export `your-export` from NFS share `share-name-or-ip` at Drive letter `R`.
