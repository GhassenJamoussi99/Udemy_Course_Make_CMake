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

##############################
##########  Targets	##########
##############################

#targetname : dependencies

build: mylib.o
	$(CPP_COMPILER_CALL) main.cc mylib.o -o $(EXECUTABLE_NAME)

#create a target bzw object file for the library
mylib.o:
	$(CPP_COMPILER_CALL) mylib.cc -c

execute:
	./$(EXECUTABLE_NAME)

clean:
	rm *.o $(EXECUTABLE_NAME)

# running "make targetname" will run it in DEBUG mode since : DEBUG ?= 1
# Explicit Debug mode (can be implicit) : make targetname DEBUG=1
# Release Mode should be explicit       : make targetname DEBUG=0
