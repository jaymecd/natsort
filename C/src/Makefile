BINARY_NAME = natsort
VERSION = 1.0.5
RELEASE_NAME = $(BINARY_NAME)-$(VERSION)
RELEASE_DIR = ./release
CC = gcc
CFLAGS = -Wall -g -Werror
PREFIX = /usr
BINDIR = $(PREFIX)/bin

all: natsort
natsort: strnatcmp.o natsort.o
	$(CC) $(CFLAGS) -o $(BINARY_NAME) strnatcmp.o natsort.o
natsort.o: natsort.c
	$(CC) $(CFLAGS) -c -o natsort.o natsort.c
strnatcmp.o: strnatcmp.c
	$(CC) $(CFLAGS) -c -o strnatcmp.o strnatcmp.c
clean:
	rm -rf $(BINARY_NAME) *.o $(RELEASE_DIR)
tarball: 
	mkdir -p $(RELEASE_DIR)/$(RELEASE_NAME)
	cp Makefile natsort.c strnatcmp.c strnatcmp.h $(RELEASE_DIR)/$(RELEASE_NAME)
	cd $(RELEASE_DIR) && tar -zcvf $(RELEASE_NAME).tar.gz $(RELEASE_NAME) 
	cd $(RELEASE_DIR) && md5sum $(RELEASE_NAME).tar.gz > $(RELEASE_NAME).tar.gz.md5
	cd $(RELEASE_DIR) && shasum $(RELEASE_NAME).tar.gz > $(RELEASE_NAME).tar.gz.sha1
install: natsort
	install -d $(BINDIR)
	install -s $(BINARY_NAME) $(BINDIR)/$(BINARY_NAME)
