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

In python, let's open a test file

```
test_file=laspy.file.File("/ufrc/ewhite/s.marconi/NeonData/2017_Campaign/D03/OSBS/L1/DiscreteLidar/ClassifiedPointCloud/NEON_D03_OSBS_DP1_412000_3283000_classified_point_cloud.laz")
```



