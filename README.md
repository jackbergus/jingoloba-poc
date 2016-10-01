[![Build Status](https://travis-ci.org/gujans/gtest-cmake-example.svg?branch=master)](https://travis-ci.org/gujans/gtest-cmake-example) [![codecov](https://codecov.io/gh/gujans/gtest-cmake-example/branch/master/graph/badge.svg)](https://codecov.io/gh/gujans/gtest-cmake-example)


# What is this?
This is an example setup of Travis-CI with cmake and google test. I finally got all three working together nicely with the help of [dmonopoly's cmake and gtest example](https://github.com/dmonopoly/gtest-cmake-example). Hopefully it'll help someone get set up with cmake and google test on travis-ci.

# Where are things?
`build/` is where code is built - like where executables are.  
`ext/` includes gtest-1.6.0.
`inlcude/` is where the header files are located (here: project1.h)
`src/` is where the source files are located (here: project1.cpp, main.cpp)
`test/` is where the test source files are located (here: test_project1.cpp)
Rest of code in root:  
-`CMakeLists.txt` must be in each subdirectory of the project  

# What do I do?

## Use it on Travis-CI:
Please look at the travis.yml file to see the setup of travis. As the gtest library is located within your project. The procedure on Travis is quite simple. Note that I used a more recent version of `cmake` as provided in the `ubuntu precise` repositories. This is needed for the relatively recent command `REMOVE_ITEM` to exclude the `main.cpp` from the source file list as I am lazy and did not want to write out the files by name.

## Use it locally: 
If you want to test it all out through the common gtest procedure, first
**delete build/** (if present). Then...

In the project root:

    mkdir build
    cd build
    cmake ..

By now Makefiles should be created.
Then, to build executables and do all that linking stuff,

    make

To prepare all your tests, run this:

    cmake -Dtest=ON ..

To run all tests easily,

    make test

Note: `cmake -DBUILD_TESTS=ON` turns on the variable 'test', which is specified in the root
CMakeLists.txt file. This is handy if you want to build in certain ways. Clear
description
[here](http://stackoverflow.com/questions/5998186/cmake-adding-command-line-options).

### Run executables
Then you can do ./myexecutable for the generated executable, e.g.:

    ./project1

and if you did cmake with test=ON:

    ./runUnitTests

# Acknowledgement and further details
This repository is based on the works of XX in [this](https://github.com/dmonopoly/gtest-cmake-example) repository. He spent a lot of time figuring out all the details for cmake and gtest. Please refer to his repository README for more detail on his approach.

