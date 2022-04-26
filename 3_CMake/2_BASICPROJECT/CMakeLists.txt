# STEPS TO COMPILE THE CODE FOR THE FIRST TIME WITH CMAKE:
# 0.) mkdir build
# 1.) cd build
# 2.) cmake ..
# 3.) make
# 4.) ./Executable

cmake_minimum_required(VERSION 3.16)

project(2_BASICPROJECT VERSION 1.0.0 LANGUAGES C CXX)
#CXX means C++

set(EXECUTABLE_NAME Executable)
set(LIBRARY_NAME Library)

add_subdirectory(src) # Bind the CMakeLists.txt of src folder
add_subdirectory(app) # Bind the CMakeLists.txt of app folder

# Course Notes
# In every folder where there's source files, we should always add
# for each one of them a CMakeLists.txt
