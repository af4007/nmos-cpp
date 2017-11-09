# Getting Started

The following instructions describe how to set up and build this software on Windows with Visual Studio 2013.
On Linux and other platforms, the steps vary slightly.

## Preparation

0. This software utilizes a number of great open-source projects  
   Set up these [external dependencies](Dependencies.md#preparation) before proceeding
1. Use CMake to configure for your platform
   - Set the CMake source directory to the [Development](../Development) directory in the nmos-cpp source tree
   - Set the CMake build directory to an appropriate location, e.g. ``.../Development/build``
   - Set CMake variables to control building nmos-cpp:
     - Set ``CMAKE_CONFIGURATION_TYPES`` (STRING) to ``Debug;Release`` to build only those configurations
     - Set ``Boost_USE_STATIC_LIBS`` (BOOL) to ``1`` (true)
   - If required, set hints for [finding Boost](https://cmake.org/cmake/help/latest/module/FindBoost.html), and C++ REST SDK and WebSocket++, for example:
     - Set ``BOOST_INCLUDEDIR`` (PATH) to the appropriate full path, e.g. ``.../boost_1_65_1`` to match the suggested ``b2`` command
     - Set ``BOOST_LIBRARYDIR`` (PATH) to the appropriate full path, e.g. ``.../boost_1_65_1/x64/lib`` to match the suggested ``b2`` command
     - Set ``cpprestsdk_DIR`` (PATH) to the location of cpprestsdk-config.cmake, e.g. ``C:/Program Files/cpprest/lib/cpprestsdk``
     - *Either* set ``websocketpp_DIR`` (PATH) to the location of websocketpp-config.cmake, e.g. ``C:/Program Files/websocketpp/cmake``
     - *Or* set ``WEBSOCKETPP_INCLUDE_DIR`` (PATH) to the location of the WebSocket++ include files, e.g. ``.../Release/libs/websocketpp`` within the C++ REST SDK source tree
2. Use CMake to generate project files  
   The "Visual Studio 12 2013 Win64" generator has been tested

## Build

Open and build the generated nmos-cpp Visual Studio Solution.

## Run Tests

All the tests are currently packaged into a single test suite, as the **nmos-cpp-registry-test** application.
This may be run automatically by building RUN_TESTS, but note that to see the output of any failed tests,
it is necessary to set ``CTEST_OUTPUT_ON_FAILURE`` to ``1`` in the environment first.

The output should be similar to the following:

```
===============================================================================
All tests passed (250 assertions in 29 test cases)
```

Note: The correct configuration of the C++ REST SDK library (e.g. cpprestsdk120_2_10.dll or cpprest120d_2_10.dll) needs to be on the ``PATH`` or copied into the output directory.

## What Next?

The [tutorial](Tutorial.md) explains how to run the NMOS Registry and some example NMOS Nodes provided by nmos-cpp.