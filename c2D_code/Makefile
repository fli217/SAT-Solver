#find OS (only Darwin and Linux are supported)
OS := $(shell uname)

EXEC_FILE = c2D

ifeq ($(OS),Darwin) 
  LIB := lib/darwin
  BIN := bin/darwin
  TEST := ../test_use/1stUIP
else ifeq ($(OS),Linux)
  LIB := lib/linux
  BIN := bin/linux
else
  $(error $(EXEC_FILE) is only supported for Mac OS and Linux, not $(OS)) 
endif

CC = gcc
CFLAGS = -g -std=c99 -O2 -Wall -finline-functions -Iinclude
LFLAGS = -L$(LIB) -lsat -lvtree -lnnf -l util -lgmp

C2D_PACKAGE = \"c2D\"
C2D_VERSION = \"1.00\"
C2D_DATE    = \"May\ 24,\ 2015\"
C2D_VERSION_FLAGS = -DC2D_PACKAGE=${C2D_PACKAGE} -DC2D_VERSION=${C2D_VERSION} -DC2D_DATE=${C2D_DATE}

SRC = src/main.c\
      src/cache.c\
      src/cnf_key.c\
      src/compile.c\
      src/count.c\
      src/utilities.c

OBJS=$(SRC:.c=.o) src/getopt.o 

c2d: $(OBJS)
	$(CC) $(CFLAGS) $(OBJS) $(LFLAGS) -o $(BIN)/$(EXEC_FILE)

%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

src/getopt.o: src/getopt.c
	$(CC) $(C2D_VERSION_FLAGS) $(CFLAGS) -c $< -o $@

clean:
	rm -f $(OBJS) $(BIN)/$(EXEC_FILE)

copy: c2d
	cp $(BIN)/$(EXEC_FILE) $(TEST)/$(EXEC_FILE)

