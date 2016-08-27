# This configuration file outlines some of the ways Arduino CMake
# can be used. For a detailed explenation of all the options please
# reade README.rst.

add_subdirectory(utils)
add_subdirectory(examples)

set(ARDUINO_DEFAULT_BOARD diecimila) # Default Board ID, when not specified
set(ARDUINO_DEFAULT_PORT /dev/ttyUSB0) # Default Port, when not specified


set(eHealth_lib_SRCS
    eHealth.cpp
    eHealthDisplay.cpp)
set(eHealth_lib_HDRS
    eHealthDisplay.h
    eHealth.h)
set(eHealth_lib_BOARD uno)
#
generate_arduino_library(eHealth_lib)


