CSRC   := $(shell ls *.cpp | grep -l ff.h * | grep -v ff.cpp | grep -v drude-fitcharge )
CSRC2  := $(shell ls *.cpp | grep -L ff.h *)
CSRC3  := $(shell ls drude-fitcharge*)
CC     := g++
CFLAGS := -g -Wno-unused-variable -Wno-write-strings
FFFILE := ff.cpp
DFFILE := drude-ff.cpp
NLLIB  := ../opt/nlopt-2.4.2/.libs/libnlopt.a
$(info $$CSRC2 is [${CSRC2}])

all: ../bin $(patsubst %.cpp, %, $(CSRC)) $(patsubst %.cpp, %.2, $(CSRC2)) $(patsubst %.cpp, %.3, $(CSRC3))
##all: ../bin $(patsubst %.cpp, %.2, $(CSRC2))
##all: ../bin $(patsubst %.cpp, %, $(CSRC)) $(patsubst %.cpp, %.2, $(CSRC2))
%: %.cpp 
	$(CC) $(CFLAGS) $< -o ../bin/$@ $(FFFILE) $(NLLIB)

%.2: %.cpp
	$(CC) $(CFLAGS) $< -o ../bin/$@ $(NLLIB)

%.3: %.cpp
	$(CC) $(CFLAGS) $< -o ../bin/$@ $(DFFILE) $(NLLIB)


../bin: 
	mkdir -p ../bin
