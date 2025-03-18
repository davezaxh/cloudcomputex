CC = gcc
CFLAGS = -Wall -Wextra -pedantic

all: firstprac

firstprac: main.o module1.o module2.o
	$(CC) $(CFLAGS) $^ -o $@

main.o: main.c module1.h
	$(CC) $(CFLAGS) -c main.c -o $@

module1.o: module1.c module1.h module2.h
	$(CC) $(CFLAGS) -c module1.c -o $@

module2.o: module2.c module2.h
	$(CC) $(CFLAGS) -c module2.c -o $@

clean:
	rm -f *.o firstprac
