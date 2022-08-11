# Tutorial3

## Let's start to create library target

- Make sure you are at correct directory under src/app/tutorial3

```
$ ls
```

- You should be able to see
  
```
README.md SConscript tutorial3.cpp
```

## Create library target

- First, we create an object file for print
  
```
g++ -c ../../lib/print/src/print.cpp -I ../../lib/print/include/
```

- You should be able to see print.o is created
- Now, we create a library target from the file

```
$ ar rvs libprint.a print.o
```

- You should be able to see libprint.a is created
  
## Create Object file

- Since tutorial3.cpp include directory where print.hpp is located, we have to include the directory as usual but this time we do not compile for print.cpp together

```
g++ -c ./tutorial3.cpp -I ../../lib/print/include/
```
## Run the program with g++

```
g++ -o <target name> <file name>
```

```
$ g++ -o tutorial3 ./tutorial3.o ./libprint.a
$ ./tutorial3
```

- You should be able to see

```
I am tutorial 3
```

## With Scons

```
$ scons -u
$ ./build/tutorial3
```