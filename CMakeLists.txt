set(CMAKE_TOOLCHAIN_FILE cmake/ArduinoToolchain.cmake) # Arduino Toolchain


cmake_minimum_required(VERSION 2.8)
#====================================================================#
#  Setup Project                                                     #
#====================================================================#
project(eHealth C CXX)

print_board_list()
print_programmer_list()

add_subdirectory(eHealth)   #add the example directory into build
