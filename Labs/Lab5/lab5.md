# Build Systems

## CMake Tutorial:
![lab5.png](lab5.png)


## Lab example

### Makefile:
all: lab_example

lab_example: main.o static_lib dynamic_lib
		gcc -lm -o lab_example main.o -L. -llib

main.o: program.c
			  gcc -O -c program.c

Source.o: source.c
			    gcc -O -c source.c

static_lib: Source.o
					  ar rcs static_lib Source.o

dynamic_lib: Source.o
						gcc -o dynamic_lib Source.0 -shared


### CMake file:
ADD_LIBRARY( static_lib STATIC source.c)

SET( APP_EXE StaticTest )

ADD_EXECUTABLE( ${APP_EXE}
                program.c )

TARGET_LINK_LIBRARIES( ${APP_EXE}
                       static_lib )
.

ADD_LIBRARY( dynamic_lib SHARED source.c)

SET( APP_EXE SharedTest )

ADD_EXECUTABLE( ${APP_EXE}
                program.c )

TARGET_LINK_LIBRARIES( ${APP_EXE}
                       dynamic_lib )
