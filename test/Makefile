include ../Makefile.inc

SRCS=$(wildcard *.c platform/posix/*.c)
SRC_COMM=$(patsubst %.c, %.o, $(SRCS))

OBJ_COMM  = $(SRC_COMM:.cpp=.o)
TARGET=test

.SUFFIXES: .o .cpp
.cpp.o:
	$(CXX) $(CXXFLAG) ${INCLUDE} -c -o $@ $<

.SUFFIXES: .o .c
.c.o:
	$(CC) $(CXXFLAG) ${INCLUDE} -c -o $@ $<


all: $(TARGET)

$(TARGET): $(OBJ_COMM) | ../lib
	$(CXX) -o $(TARGET) $(OBJ_COMM) -L../lib -lbbr -lcc -lcommon -lestimator -lpacing -lpthread

../lib:
	mkdir ../lib
  
depend:
	mkdep $(CXXFLAG) $(SRC_COMM)

install:

clean: 
	rm -f *.o $(TARGET) 
