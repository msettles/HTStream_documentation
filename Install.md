---
title: Installation
order: 1
---

# Installing HTStream version 1.2.0

## Install binaries for linux systems:

On Linux systems, the easiest and most straight forward option is to download and unpack the pre-compiled binaries to somewhere on your `$PATH`.

```bash
wget https://github.com/ibest/HTStream/releases/download/v1.2.0-release/HTStream_v1.2.0-release.tar.gz

tar xvf HTStream_v1.2.0-release.tar.gz
```

## Install from Bioconda:

HTStream is available through the Bioconda channel. Visit [Miniconda](https://docs.conda.io/en/latest/miniconda.html).

```bash
conda install -c bioconda htstream
```

## Compiling HTStream from source

### Prerequisites:
- Cmake 3.2 or greater.
- Boost 1.56 or greater including the following
    - libboost-dev
    - libboost-system-dev
    - libboost-program-options-dev
    - libboost-iostreams-dev
    - libboost-filesystem-dev

On Debian based systems (e.g. Ubuntu) prerequisites can be installed as follows
```bash
sudo apt-get install cmake
sudo apt install libboost-dev libboost-system-dev libboost-program-options-dev libboost-iostreams-dev libboost-filesystem-dev
```

on Mac OSX using [Homebrew](https://brew.sh/)
```bash
brew upgrade
brew install cmake
brew install boost
```

Alternatively Boost can be installed from source:
```bash
wget -O 1_60.tar.bz2 https://sourceforge.net/projects/boost/files/boost/1.60.0/boost_1_60_0.tar.bz2/download
tar --bzip2 -xf 1_60.tar.bz2
cd boost_1_60_0
./bootstrap.sh
./b2
BOOST_INCLUDE=$(pwd)
BOOST_INCLUDE_LIB=$(pwd)/stage/lib
```

### Compiling HTStream from source

Downloading the current release version
```bash
wget -O HTStream-v1.2.0-release.zip https://github.com/ibest/HTStream/archive/v1.2.0-release.zip
unzip HTStream-v1.2.0-release.zip
cd HTStream-1.2.0-release
```

**OR** Downloading the current development version
```bash
git clone https://github.com/ibest/HTStream.git
cd HTStream
```

Compiling the source code with cMake and make
```bash
mkdir build
cd build
cmake ..
make
make test
make install
```

default install prefix is /usr/local/bin which may require super user or sudo access
{:.danger}

### Optional cmake parameters

When using an alternative Boost install location
```bash
cmake -DCMAKE_INCLUDE_PATH=$BOOST_INCLUDE -DCMAKE_LIBRARY_PATH=$BOOST_INCLUDE_LIB ..
```

To specify an different install prefix
```bash
cmake -DCMAKE_INSTALL_PREFIX=/path/to/install ..
```

Building binaries with statically linked libraries

```bash
cmake -DBUILD_STATIC_BIN=ON ..
```

#### Troubleshooting

Some users have experienced issues with the boost install. We think this arises from having other versions of boost on the system. Try the following:

```bash
cmake -DBoost_NO_SYSTEM_PATHS=TRUE -DBOOST_INCLUDEDIR=/usr/local/include/ ..
```

**Or try**

```bash
export CC=`which gcc`
export CXX=`which g++`
mkdir -p build
cd build
cmake -DBoost_NO_SYSTEM_PATHS=TRUE -DCMAKE_INCLUDE_PATH=$BOOST_INCLUDE -DCMAKE_LIBRARY_PATH=$BOOST_INCLUDE_LIB ..
make
make test
make install
```
