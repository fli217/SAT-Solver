CC = gcc
CFLAGS = -std=c99 -O2 -Wall -finline-functions -Iinclude
LIBRARY_FLAGS = -Llib -lsat
EXEC_FILE = sat 
TEST = ../test_use/1stUIP

SRC = src/main.c

OBJS=$(SRC:.c=.o)

HEADERS = sat_api.h

sat: $(OBJS)
	$(CC) $(CFLAGS) $(OBJS) $(LIBRARY_FLAGS) -o $(EXEC_FILE)

%.o: %.c $(HEADERS)
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	rm -f $(OBJS) $(EXEC_FILE)

copy: sat
	cp $(EXEC_FILE) $(TEST)/$(EXEC_FILE)
