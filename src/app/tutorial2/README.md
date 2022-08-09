# Tutorial2

## Let's start to include other directory

* Make sure you are at correct directory under src/app/tutorial2

```
$ ls 
```

* You should be able to see

```
print README.md SConscript tutorial2.cpp
```

## Method in tutorial1 would not work

```
$ g++ -o tutorial2 ./tutorial2.cpp
```

## Create Object file

* since tutorial2.cpp include directory where print.hpp is located and the implementation of function exposed in print.hpp is located at print.cpp, hence we have to compile both print.cpp and tutorial2.cpp

```
g++ -c ./print/src/print.cpp ./tutorial2.cpp -I ./print/include/
```

## Run the program with g++

```
g++ -o <target name> <file name>
```

```
$ g++ -o tutorial2 ./tutorial2.o ./print.o
$ ./tutorial2
```

* You should be able to see

```
I am tutorial 2
```

## With Scons

```
$ scons -u
$ ./build/tutorial2
```