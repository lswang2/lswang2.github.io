OpenRISC Tool chain
===================

* newlib based tool chain : binutils + gcc + newlib
  * build binutils
  * build gcc first stage
  * build newlib
  * build gcc second stage

* glibc based tool chain : binutils + gcc + glibc
* musl cross : binutils + gcc + musl

# Using toolchain by docker
    $ docker pull lswang2/build-tools
    $ docker run --rm -it -v `pwd`:/work lswang2/build-tools
    root@......:/work#

# binutils-gdb

**need tools**

    $ build-essential autoconf flex bison gperf libgmp-dev libmpfr-dev libmpc-dev zlib1g-dev texinfo guild-1.8

**get source**

    $ git clone git://github.com/lswang2/binutils-gdb

**prepare**

    $ mkdir build-binutils
    $ cd build-binutils

**configure**

    $ ../binutils-gdb/configure --target=or1k-elf --prefix=/usr/local/or1k --enable-shared \
    --disable-itcl --disable-tk --disable-tcl --disable-winsup --disable-libgui --disable-rda \
    --disable-sid --disable-sim --enable-gdb --with-sysroot --disable-newlib --disable-libgloss \
    --disable-werror
    
**note:**
on 32-bit machines --disable-werror is needed due to an enum acting as bit mask is considered signed

**build**

    $ make
    $ make install

# newlib

**get source**

    $ git clone git://github.com/openrisc/newlib

**BSP modification**

    board에 맞추어 BSP를 적용하려면
    libgloss/or1k/boards/new_bsp.S 파일을 생성하고
    libgloss/or1k/Makefile.in 에서 BOARDS를 새 파일만 지정도록 수정한다

**prepare**

    $ mkdir build-newlib
    $ cd build-newlib

**configure**

    $ ../newlib/configure --target=or1k-elf --prefix=/usr/local/or1k --enable-shared --disable-itcl \
    --disable-tk --disable-tcl --disable-winsup --disable-libgui --disable-rda --disable-sid --enable-sim \
    --disable-or1ksim --enable-gdb --with-sysroot --enable-newlib --enable-libgloss --disable-werror

**build**

    $ make
    $ export PATH=$PATH:/usr/local/or1k/bin
    $ make install

# gcc

**get source**

    $ git clone git://github.com/openrisc/or1k-gcc

## first stage

**prepare**

    $ mkdir build-gcc
    $ cd build-gcc

**configure**

    $ ../or1k-gcc/configure --target=or1k-elf --prefix=/usr/local/or1k --enable-languages=c \
    --disable-shared --disable-libssp

**build**

    $ make
    $ make install

## second stage

**prepare**

    $ mkdir build-gcc2
    $ cd build-gcc2

**configure**

    $ ../or1k-gcc/configure --target=or1k-elf --prefix=/usr/local/or1k --enable-languages=c \
    --disable-shared --disable-libssp --with-newlib

**build**

    $ make
    $ make install

# musl cross

Lightweight linux library.

# glibc

This is for full linux porting.

