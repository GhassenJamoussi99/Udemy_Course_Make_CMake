# STEPS TO COMPILE THE CODE FOR THE FIRST TIME WITH CMAKE:
# 0.) mkdir build
# 1.) cd build
# 2.) cmake ..
# 3.) make
# 4.) ./Executable

cmake_minimum_required(VERSION 3.16)

project(2_BASICPROJECT VERSION 1.0.0 LANGUAGES C CXX)
#CXX means C++

##################### VARIABLES ######################

set(CMAKE_CXX_STANDARD          17)  # C++17
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS        OFF)

######################################################

set(EXECUTABLE_NAME Executable)
set(LIBRARY_NAME Library)

option(COMPILE_EXECUTABLE "Whether to compile the executable or not" ON) # ON means yes

add_subdirectory(src) # Bind the CMakeLists.txt of src folder
if (COMPILE_EXECUTABLE)
    add_subdirectory(app) # Bind the CMakeLists.txt of app folder
endif()

# Course Notes
# - In every folder where there's source files, we should always add
# for each one of them a CMakeLists.txt.
# - COMPILE_EXECUTABLE option can be used for unittests; if we want
# to run it with the main project we can set to on otherwise off.
# or we can use it by passing options
# Passing Options
# If you have set some options in the CMakeLists, you can pass values in the command line.
# cd build
# cmake -DMY_OPTION=[ON|OFF] .. e.g in our case : cmake -DCOMPILE_EXECUTABLE=ON
