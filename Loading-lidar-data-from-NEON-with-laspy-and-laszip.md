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
git checkout tags/2.0.2
cd LASzip
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

Add your paths

```
export LD_LIBRARY_PATH="/home/b.weinstein/LASzip/build/lib:$LD_LIBRARY_PATH"
export PATH="/home/b.weinstein/LASzip/build/bin:$PATH"
```

Make sure it works locally

```
(pangeo) [b.weinstein@c30a-s26 bin]$ pwd
/home/b.weinstein/LASzip/build/bin
(pangeo) [b.weinstein@c30a-s26 bin]$ laszip-config --version
2.0.2
```

Go to a new directory to test linking

```
cd ~
(pangeo) [b.weinstein@c30a-s26 ~]$ laszip-config --version
2.0.2
```

Looking good.

# Install laspy

```
pip install laspy
```

#Install command line utilities

```
wget http://lastools.org/download/LAStools.zip
unzip LAStools.zip
cp laszip ~/LASzip/build/bin/
cd LAStools
module load gcc
make
```
# Move utilities over to LASzip repo

```
cp laszip ~/LASzip/build/bin/
cd ~/LASzip/build/bin/
ln -s ~/LASzip/build/bin/laszip ~/LASzip/build/bin/laszip-cli
```

test it

```
[b.weinstein@gator3 bin]$ ./laszip-cli
./laszip-cli is better run in the command line
enter input file: 
```

great!

Add to path

```
[b.weinstein@gator3 bin]$ PATH=$PATH:$(pwd)
```

# Test file

```
[b.weinstein@gator3 bin]$ python
Python 3.6.4 |Anaconda, Inc.| (default, Jan 16 2018, 18:10:19) 
[GCC 7.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import laspy
>>> test_file=laspy.file.File("/ufrc/ewhite/s.marconi/NeonData/2017_Campaign/D03/OSBS/L1/DiscreteLidar/ClassifiedPointCloud/NEON_D03_OSBS_DP1_412000_3283000_classified_point_cloud.laz")
>>> test_file
<laspy.file.File object at 0x2ac276505fd0>
```

TODO: add path on every worker using .bashrc file.