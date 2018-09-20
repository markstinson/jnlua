# Paths
JDK_DIR=/System/Library/Frameworks/JavaVM.framework/Versions/Current
LUA_DIR=../../../../lua/lua-5.3.4_MacOS1011_lib
VERSION=53

# Tools
CC=gcc
LD=gcc

# Default arguments
CFLAGS=-c -fno-strict-aliasing -m64 -fPIC -O2 -Wall -DNDEBUG -D_REENTRANT -DLUA_USE_LINUX
LDFLAGS=-dynamiclib -m64

# Description blocks
all: libjnlua$(VERSION).dylib

libjnlua$(VERSION).dylib: jnlua.o
	$(LD) $(LDFLAGS) -o libjnlua$(VERSION).dylib -lc jnlua.o $(LUA_DIR)/liblua53.a

jnlua.o: ../jnlua.c
	$(CC) $(CFLAGS) -I$(JDK_DIR)/Headers -I $(LUA_DIR)/include ../jnlua.c

clean:
	-rm libjnlua$(VERSION).dylib jnlua.o
