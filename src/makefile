CC=g++
CFLAGS=-c -std=c++0x -Wall -Werror
LDFLAGS=

EXEC=iskat
SOURCES=main.cpp
HEADERS=
OBJECTS=$(SOURCES:.cpp=.o)

DBGDIR = build/debug
DBGOBJS = $(addprefix $(DBGDIR)/, $(OBJECTS))
DBGCFLAGS = -g3 -O0 -DDEBUG

RELDIR = build/release
RELOBJS = $(addprefix $(RELDIR)/, $(OBJECTS))
RELCFLAGS = -O3 -DNDEBUG

.PHONY: all clean debug prep release rebuild install tgz

default: prep release

release: $(RELOBJS)
	$(CC) $(LDFLAGS) -o $(EXEC) $(RELOBJS)

debug: $(DBGOBJS)
	$(CC) $(LDFLAGS) -o $(EXEC) $(DBGOBJS)

$(DBGDIR)/%.o: %.cpp
	$(CC) $(CFLAGS) $(DBGCFLAGS) -o $@ $<

$(RELDIR)/%.o: %.cpp
	$(CC) $(CFLAGS) $(RELCFLAGS) -o $@ $<

rebuild: clean default

clean:
	rm -vf $(EXEC) $(RELOBJS) $(DBGOBJS)

install: $(EXEC)
	cp $(EXEC) /usr/bin/

tgz:
	tar -cvzf ../bin/iskat.tgz $(SOURCES) $(HEADERS) makefile

prep:
	@mkdir -p $(DBGDIR) $(RELDIR)