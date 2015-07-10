CC=g++
CFLAGS=-c -std=c++0x -Wall -Werror
LDFLAGS=
EXEC=../bin/iskat
SOURCES=main.cpp
OBJECTS=$(SOURCES:.cpp=.o)

default: $(SOURCES) $(EXEC)
	
$(EXEC): $(OBJECTS) 
	$(CC) $(LDFLAGS) $(OBJECTS) -o $@

.cpp.o:
	$(CC) $(CFLAGS) $< -o $@

clean:
	rm -rf *.o $(EXEC)

install:
	cp $(EXEC) /usr/bin/