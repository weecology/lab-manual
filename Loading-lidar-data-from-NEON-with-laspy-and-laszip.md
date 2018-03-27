The current best practices is to use laspy to read .laz data provided by NEON.
To do this we need to install [laszip](https://www.laszip.org/) on hipergator. We do not have root permissions, so we'll need to install from source and link the libraries. I am assuming we are working within a conda env (see). 

Thanks to http://scigeo.org/articles/howto-install-latest-geospatial-software-on-linux.html#compile_laszip for helpful doc.

```
source activate pangeo
```

# Install laszip from source

```
module load git
git clone https://github.com/LASzip/LASzip.git
cd LASzip
git checkout tags/2.0.2
```

Make files in the build directory.
```
mkdir build
cd build
module load cmake
module load gcc
cmake .. -DCMAKE_INSTALL_PREFIX=/home/b.weinstein/LASzip/build 
```

Build target

```
make
```

Install

```
make install
```

# Install command line utilities

```
cd ~
wget http://lastools.org/download/LAStools.zip
unzip LAStools.zip
rm LAStools.zip
cd LAStools
make
```
## Move utilities over to LASzip repo

```
cd /home/b.weinstein/LAStools/bin
cp laszip /home/b.weinstein/LASzip/build/bin/
cd /home/b.weinstein/LASzip/build/bin/
ln -s /home/b.weinstein/LASzip/build/bin/laszip /home/b.weinstein/LASzip/build/bin/laszip-cli
```

## Test it locally.

```
[b.weinstein@gator3 bin]$ ./laszip-cli
./laszip-cli is better run in the command line
enter input file: 
```


Add your paths so that python can find it globally.

```
export LD_LIBRARY_PATH="/home/b.weinstein/LASzip/build/lib:$LD_LIBRARY_PATH"
export PATH="/home/b.weinstein/LASzip/build/bin:$PATH"
```

Go to a new directory to test linking

```
cd ~
laszip-cli -h
```

This should return information about the client library.

# Install laspy

Python package for manipulating lidar data.

```
pip install laspy
```


# Test file within python

```
[b.weinstein@gator3 bin]$ python
Python 3.6.4 |Anaconda, Inc.| (default, Jan 16 2018, 18:10:19) 
[GCC 7.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
import laspy
test_file=laspy.file.File("/ufrc/ewhite/s.marconi/NeonData/2017_Campaign/D03/OSBS/L1/DiscreteLidar/ClassifiedPointCloud/NEON_D03_OSBS_DP1_412000_3283000_classified_point_cloud.laz")
>>> test_file
<laspy.file.File object at 0x2ac276505fd0>
```
