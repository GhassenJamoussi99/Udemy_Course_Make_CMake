# STEPS TO COMPILE THE CODE WITH CMAKE:
# 0.) mkdir build
# 1.) cd build
# 2.) cmake ..
# 3.) make
# 4.) ./Executable

cmake_minimum_required(VERSION 3.16)

project(HelloWorld VERSION 1.0.0 LANGUAGES C CXX)
#CXX means c++

add_executable(Executable main.cc)
