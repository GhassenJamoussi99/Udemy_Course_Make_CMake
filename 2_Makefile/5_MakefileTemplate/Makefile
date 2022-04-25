##############################
########  VARIABLES  #########
##############################

#if we didn't set the debug value then it will be by default 1
#Achtung:Makefile mag Kommentare in der Zeile einer Variable nicht.
#Das heisst nicht Kommentare neben Debug Variable schreiben, ansonsten
#führt das zu Problemen ('?=' kann ignoriert werden)

DEBUG ?= 1
ifeq ($(DEBUG),1)
#debug mode
CPP_COMPILER_FLAGS = -g -O0 -Wall -Wextra -Wpedantic -Wconversion -std=c++17
EXECUTABLE_NAME = mainDebug
else
#release mode
CPP_COMPILER_FLAGS = -O3 -Wall -Wextra -Wpedantic -Wconversion -std=c++17
EXECUTABLE_NAME = mainRelease
endif

CPP_COMPILER = g++
CPP_COMPILER_CALL = $(CPP_COMPILER) $(CPP_COMPILER_FLAGS)

INCLUDE_DIR = include
SOURCE_DIR = src
BUILD_DIR = build

CPP_SOURCES = $(wildcard $(SOURCE_DIR)/*.cpp)
CPP_OBJECTS = $(patsubst $(SOURCE_DIR)/%.cpp, $(BUILD_DIR)/%.o, $(CPP_SOURCES))

CC_SOURCES = $(wildcard $(SOURCE_DIR)/*.cc)
CC_OBJECTS = $(patsubst $(SOURCE_DIR)/%.cc, $(BUILD_DIR)/%.o, $(CC_SOURCES))

# HOW wildcard works
# The use of wildcard card function in make file is
# to list all the source files with a particular extension.

# HOW patsubst works
# if you want to convert .c files to .o files then patstubst is useful.

##############################
######  PSEUDO TARGETS	######
##############################
build: $(BUILD_DIR)/$(EXECUTABLE_NAME)

##############################
##########  TARGETS	##########
##############################

#targetname : dependencies

# OBJECT FILES to an EXECUTABLE : %.o -> %.exe/out

TARGET_DEPS = $(CPP_OBJECTS) $(CC_OBJECTS)
$(BUILD_DIR)/$(EXECUTABLE_NAME): $(TARGET_DEPS)
	$(CPP_COMPILER_CALL) $^ -o $@

# With "$^" being the name of all dependencies ($(CPP_OBJECTS) $(CC_OBJECTS))
# And "$@" being the file name of the target ( $(EXECUTABLE_NAME) )
# Bonus : "$<" means the name of the first dependency

execute:
	.$(BUILD_DIR)/$(EXECUTABLE_NAME)

##############################
#########  PATTERNS ##########
##############################

#create a target bzw object file for the libraries

#specific
#mylib.o:
#	$(CPP_COMPILER_CALL) mylib.cc -c

#general
# "%.o: %.cpp" means that any file ending in .o depends
# on the same filename ending in .cpp to be present.

# SOURCE FILES to OBJECT FILES : %.cc/cpp -> %.o
$(BUILD_DIR)/%.o: $(SOURCE_DIR)/%.cpp
	$(CPP_COMPILER_CALL) -I $(INCLUDE_DIR) -c $< -o $@

$(BUILD_DIR)/%.o: $(SOURCE_DIR)/%.cc
	$(CPP_COMPILER_CALL) -I $(INCLUDE_DIR) -c $< -o $@

# "$<" means the name of the first dependency (which is in our case "%.cpp/cc")
# "$@" being the file name of the target ( $(EXECUTABLE_NAME) )

# --> The -c flag says to generate the object file, the -o $@ says to put
# the output of the compilation in the file named on the left side of
# the ":" (%.o) <--

clean:
	rm -rf $(BUILD_DIR)/*.o $(BUILD_DIR)/$(EXECUTABLE_NAME)

# -rf will remove the directory if it's present.


# Notes:
# running "make targetname" will run it in DEBUG mode since : DEBUG ?= 1
# Explicit Debug mode (can be implicit) : make targetname DEBUG=1
# Release Mode should be explicit       : make targetname DEBUG=0

#TODO
#
#
