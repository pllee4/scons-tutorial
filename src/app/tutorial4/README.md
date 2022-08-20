# Tutorial4

## Let's start to create shared library target

- Shared library is slightly different from normal static library.
- Static library(.a) can be linked directly into the final executable produced by the linker, it is contained in it and there is no need to have the library into the system where the executable will be deployed.
- Shared library(.so) is linked but not embedded in the final executable, so will be loaded when the executable is launched and need to be present in the system where the executable is deployed.
  
- Make sure you are at correct directory under src/app/tutorial4

```
$ ls
```

- You should be able to see

```
print README.md SConscript tutorial4.cpp
```

## Create shared library target

```
$ g++ -c -fpic print/src/print.cpp -I ./print/include/

$ g++ -shared -o libprint.so print.o
```

## Run the program with g++

```
$ g++ -L$PWD -o tutorial4 tutorial4.cpp -lprint -I ./print/include/
$ ./tutorial4
```
- You would see the error below

```
./tutorial4: error while loading shared libraries: libprint.so: cannot open shared object file: No such file or directory
```
- This is because the path of the shared libary is not known.
  
```
$ export LD_LIBRARY_PATH=$PWD:$LD_LIBRARY_PATH
$ ./tutorial4
```

- You should be able to see

```
I am tutorial4
```

- You can find those shared library installed in your computer at /usr/lib

## With Scons

- please ignore the warning for now
```
$ scons -u
$ export LD_LIBRARY_PATH=$PWD/build/print:$LD_LIBRARY_PATH
$ ./build/tutorial4
```