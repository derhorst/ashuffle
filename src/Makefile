.PHONY: clean

QUIET_CC = @printf ' CC %b\n' $@;
old_cc := $(CC)
CC = $(QUIET_CC)$(old_cc)

CFLAGS = -std=c99 -Wall -Wextra -pedantic
libs = libmpdclient

# For library linkage
CFLAGS += $(shell pkg-config $(libs) --cflags)
LDLIBS = $(shell pkg-config $(libs) --libs)

objects = $(patsubst %.c,%.o,$(wildcard *.c))

ashuffle: $(objects)

list.o: list.h
rule.o: rule.h list.h
args.o: args.h rule.h list.h
shuffle.o: shuffle.h list.h
getpass.o: getpass.h

gdb: ashuffle
	gdb ./ashuffle

clean: 
	-rm $(objects) ashuffle
