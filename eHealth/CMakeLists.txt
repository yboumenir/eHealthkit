# This configuration file outlines some of the ways Arduino CMake
# can be used. For a detailed explenation of all the options please
# reade README.rst.

add_subdirectory(utils)
add_subdirectory(examples)


MESSAGE(STATUS "garbage: " ${ARDUINO_SDK_PATH})

set(eHealth_lib_SRCS
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/CDC.cpp
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/HardwareSerial.cpp
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/HID.cpp
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/IPAddress.cpp
#    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/main.cpp
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/new.cpp
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/Print.cpp
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/Stream.cpp
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/Tone.cpp
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/USBCore.cpp
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/WInterrupts.c
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/wiring_analog.c
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/wiring.c
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/wiring_digital.c
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/wiring_pulse.c
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/wiring_shift.c
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/WMath.cpp
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/WString.cpp
    eHealth.cpp
    eHealthDisplay.cpp
    )

set(eHealth_lib_HDRS
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/Arduino.h
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/binary.h
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/Client.h
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/HardwareSerial.h
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/IPAddress.h
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/new.h
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/Platform.h
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/Printable.h
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/Print.h
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/Server.h
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/Stream.h
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/Udp.h
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/USBAPI.h
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/USBCore.h
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/USBDesc.h
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/WCharacter.h
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/wiring_private.h
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/WString.h
    eHealthDisplay.h
    eHealth.h
    )

set(eHealth_lib_BOARD uno)

include_directories(
    ${ARDUINO_SDK_PATH}/hardware/arduino/cores/arduino/
    ${ARDUINO_SDK_PATH}/hardware/arduino/variants/standard/
    ${CMAKE_CURRENT_SOURCE_DIR}
    )

#
generate_arduino_library(eHealth_lib)

MESSAGE(STATUS "garbage: " ${eHealth_lib_SRCS})
MESSAGE(STATUS "garbage: " ${CMAKE_CURRENT_SOURCE_DIR})

# Alternative: by variables
set(eHealth_SRCS examples/ECGExampleKST/ECGExampleKST.cpp)
set(eHealth_LIBS eHealth_lib)
set(eHealth_BOARD uno)
#
#generate_arduino_firmware(blink)

generate_arduino_firmware(eHealth)


