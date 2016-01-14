# Build Instructions

FBOSS is being tested on Ubuntu 14.04.

The provided `getdeps.sh` script will fetch the dependencies required. If you are
running on Ubuntu or Debian, and would like to install the software available
available as Ubuntu packages, `getdeps.sh pkg` will fetch and install the packages.
This needs sudo. Without arguments, getdeps.sh will update or fetch source dependencies
and build them.

If you want to build them manually, the dependencies are as follows:

* [folly](https://github.com/facebook/folly), built from source and installed
* folly's own prerequisites: double-conversion, gflags, and glog
* [fbthrift](https://github.com/facebook/fbthrift), built from source and
  installed
* iproute2-3.19.0: download from
  [here](https://www.kernel.org/pub/linux/utils/net/iproute2/iproute2-3.19.0.tar.xz)
* Broadcom's [OpenNSL](https://github.com/Broadcom-Switch/OpenNSL)

Once the prerequisites are available, take the following steps. 

Clone the repository:

```
git clone https://github.com/facebook/fboss.git
```
 
If you installed dependencies manually, CMAKE_INCLUDE_PATH and
CMAKE_LIBRARY_PATH must be modified to include the paths to the dependencies.
If you use `getdeps.sh`, then this should work out of the box.

Build as follows:

```
mkdir fboss/build
cd fboss/build
cmake ..
make
```

The produced executables are `sim_agent` and `wedge_agent` in the build directory.
