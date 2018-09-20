# Paths
JDK_DIR=/usr/lib/jvm/java-8-openjdk-amd64
LUA_DIR=../../../../lua/lua-5.3.4_Linux44_64_lib
VERSION=53
ARCH=amd64

# Tools
CC=gcc
LD=gcc

# Default arguments
CFLAGS=-c -fno-strict-aliasing -fPIC -O2 -Wall -DNDEBUG -D_REENTRANT -DLUA_USE_LINUX
LDFLAGS=-shared

# Description blocks
all: libjnlua$(VERSION).so javavm.so

libjnlua$(VERSION).so: jnlua.o
	$(LD) $(LDFLAGS) -Wl,-soname=libjnlua$(VERSION).so -o libjnlua$(VERSION).so jnlua.o $(LUA_DIR)/liblua$(VERSION).a

jnlua.o: ../jnlua.c
	$(CC) $(CFLAGS) -I$(JDK_DIR)/include -I$(JDK_DIR)/include/linux -I$(LUA_DIR)/include ../jnlua.c

javavm.so: javavm.o
	$(LD) $(LDFLAGS) -Wl,-soname=javavm.so -o javavm.so javavm.o $(LUA_DIR)/liblua$(VERSION).a

javavm.o: ../javavm.c ../javavm.h
	$(CC) $(CFLAGS) -I$(JDK_DIR)/include -I$(JDK_DIR)/include/linux -I$(LUA_DIR)/include ../javavm.c

clean:
	-rm libjnlua$(VERSION).so jnlua.o
	-rm javavm.so javavm.o
