TARGET=sall.out
OBJS=test.o src/mystring.o src/bitmask.o src/myutils.o

TOPDIR=${PWD}
CFLAGS=-I${TOPDIR}/include
LDFLAGS=-lmystr -lmyutils -lmasking
LIBPATH=${PWD}

all:sall.out

sall.out:test.o libmystr.a libmyutils.a libmasking.a
	gcc -L${LIBPATH} $< -o $@ ${LDFLAGS} -static
libmystr.a:src/mystring.o 
	ar rc $@ $^
libmyutils.a:src/myutils.o 
	ar rc $@ $^
libmasking.a:src/bitmask.o 
	ar rc $@ $^
	
%.o:src/%.c include/%.h

test.o: test.c include/*.h
test:sall.out
	./sall.out

clean:
	rm -rf *.a *.o src/*.o ${TARGET}
