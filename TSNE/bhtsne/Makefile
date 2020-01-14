UNAME := $(shell uname)
ifeq ($(UNAME),Linux)
	SHAREDLIB_EXT := so
	SHAREDLIB_FLAG := -shared
endif
ifeq ($(UNAME),Darwin)
	SHAREDLIB_EXT := dylib
	SHAREDLIB_FLAG := -dynamiclib
endif

CURDIR := $(shell pwd)
LIBNAME := $(CURDIR)/sharedlib_tsne.$(SHAREDLIB_EXT)

CXXFLAGS:= -std=c++0x -U__STRICT_ANSI__ -O3 -fPIC -c
OBJS= tsne_main.o tsne.o sptree.o
all: tsne

.PHONY: all clean

tsne:
	g++ $(CXXFLAGS) sptree.cpp tsne.cpp tsne_main.cpp
	g++ $(SHAREDLIB_FLAG) -o $(LIBNAME) $(OBJS)
	
clean:
	$(RM) -rf $(OBJS) tsne
	$(RM) -rf $(LIBNAME) tsne