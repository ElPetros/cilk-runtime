```
Intel(R) Cilk(TM) Plus runtime library

Part 1: Building with automake
------------------------------

Index:
1. BUILDING
2. USING
3. DOXYGEN DOCUMENTATION
4. QUESTIONS OR BUGS
5. CONTRIBUTIONS

#
#  1. BUILDING:
#

To distribute applications that use the Intel Cilk Plus language
extensions to non-development systems, you need to build the Intel
Cilk Plus runtime library and distribute it with your application.

To build the libcilkrts.so runtime library component, you need the
autoconf and automake packages, which are available through your
favorite package manager.  You also need a C/C++ compiler that
supports the Intel Cilk Plus language extensions, since the runtime
uses Intel Cilk Plus features internally.  Use either the Intel(R)
C++ Compiler (icc command) v12.1 or later, or in GCC 4.9 or later
(gcc command).

Once you have the necessary prerequisites installed, you can use the
following commands to create the library:

% libtoolize
% aclocal
% automake --add-missing
% autoconf
% ./configure
% make
% make install

This will produce the libcilkrts.so shared object.  To install the
library in a custom location, set the prefix while running the
configure script:

% ./configure --prefix=/your/path/to/lib

It is also possible to use CMake if the above method does not apply
well in your environment. Instruction is available in CMakeLists.txt.

#
#  2. USING:
#

The Intel(R) C++ Compiler will automatically try to bring in the
Intel Cilk Plus runtime in any program that uses the relevant
features.  GCC requires explicit linking of both the library and
its dependencies (libpthread, libdl).  For example:

% gcc foo.c -lcilkrts -lpthread -ldl

#
#  3. DOXYGEN DOCUMENTATION:
#

The library source has Doxygen markup.  Generate HTML documentation
based on the markup by changing directory into runtime and running:

% doxygen doxygen.cfg

#
#  4. QUESTIONS OR BUGS:
#

Issues with the Intel Cilk Plus runtime can be addressed in the Intel
Cilk Plus forums:
http://software.intel.com/en-us/forums/intel-cilk-plus/

#
#  5. CONTRIBUTIONS:
#

The Intel Cilk Plus runtime library is dual licensed. The upstream copy
of the library is maintained via the BSD-licensed version available at:
http://cilkplus.org/

Changes to the Intel Cilk Plus runtime are welcome and should be
contributed to the upstream version via http://cilkplus.org/.

Thanks to Tobias Burnus for showing us the magic to make gcc and g++
automatically include the Cilk Plus runtime.

Part 2: Building with cmake
---------------------------

Index:
1. BUILDING
2. USING
3. DOXYGEN DOCUMENTATION
4. QUESTIONS OR BUGS
5. CONTRIBUTIONS

#
#  1. BUILDING:
#

To distribute applications that use the Intel Cilk Plus language
extensions to non-development systems, you need to build the Intel
Cilk Plus runtime library and distribute it with your application.
This instruction describes the build process using CMake*, which
supports Linux*, Windows*, and OS X*.  It is fine to use this process
to build a Linux library, but it is highly recommended to use the
more mature build process described in README.automake when building
on Linux.

You need the CMake tool and a C/C++ compiler that supports the Intel
Cilk Plus language extensions, and the requirements for each operating
systems are:

Common:
    CMake 3.0.0 or later
    Make tools such as make (Linux, OS X) or nmake (Windows)
Linux:
    GCC* 4.9.2 or later, or Intel(R) C++ Compiler v12.1 or later
Windows:
    Intel C++ Compiler v12.1 or later
    Visual Studio* 2010 or later
OS X:
    Cilk-enabled branch of Clang*/LLVM* (http://cilkplus.github.io),
    or Intel C++ Compiler v12.1 or later

The common steps to build the libraries are 1) invoke cmake with
appropriate options, 2) invoke a make tool available on the system.
The following examples show build processes on OS X and Windows.

OS X:
    % mkdir ./build && cd ./build
    % cmake -DCMAKE_C_COMPILER=clang -DCMAKE_CXX_COMPILER=clang++ \
            -DCMAKE_INSTALL_PREFIX=./install ..
    % make && make install

Windows:
    % mkdir .\build && cd .\build
    % cmake -G "NMake Makefiles" -DCMAKE_C_COMPILER=icl \
            -DCMAKE_CXX_COMPILER=icl -DCMAKE_INSTALL_PREFIX=.\install ..
    % nmake && nmake install

#
#  2. USING:
#

The Intel(R) C++ Compiler will automatically try to bring in the
Intel Cilk Plus runtime in any program that uses the relevant
features.  GCC and Clang requires an explicit compiler option,
-fcilkplus, to enable Intel Cilk Plus language extensions.
For example,

% gcc -fcilkplus -o foo.exe foo.c
% clang -fcilkplus -o foo.exe foo.c

#
#  3. DOXYGEN DOCUMENTATION:
#

The library source has Doxygen markup.  Generate HTML documentation
based on the markup by changing directory into runtime and running:

% doxygen doxygen.cfg

#
#  4. QUESTIONS OR BUGS:
#

Issues with the Intel Cilk Plus runtime can be addressed in the Intel
Cilk Plus forums:
http://software.intel.com/en-us/forums/intel-cilk-plus/

#
#  5. CONTRIBUTIONS:
#

The Intel Cilk Plus runtime library is dual licensed. The upstream copy
of the library is maintained via the BSD-licensed version available at:
http://cilkplus.org/

Changes to the Intel Cilk Plus runtime are welcome and should be
contributed to the upstream version via http://cilkplus.org/.

------------------------
Intel and Cilk are trademarks of Intel Corporation in the U.S. and/or
other countries.

*Other names and brands may be claimed as the property of others.
```