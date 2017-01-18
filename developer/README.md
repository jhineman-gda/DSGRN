# Developer installation procedure #

## Using provided installation shell scripts ##

### Build the dsgrn ###

1. Clone repository
2. cd to Directory
3. run ./.install/boost.sh, ./.install/delegator.sh ./.install/openmpi.sh ./sqlite3.sh
4. cmake -DCMAKE_INSTALL_PREFIX=/home/<username>/.local .
5. check boost by examining CMakeCache.txt (edit if necessary)
6. make install
7. At this point dsgrn should work and one should be able

### Build the NetworkLogic ###

1. cd software/NetworkLogic
2. cmake -DCMAKE_INSTALL_PREFIX=/home/<username>/.local .
3. make install
4. At this point dsgrn should work and you should be able to
follow the tutorial at shaunharker.github.io/DSGRN/ for example
    $ which dsgrn
    /home/<username>/.local/bin/dsgrn
    $ dsgrn network ./networks/2D_Example_C.txt
    $ dsgrn parameter
    There are 1600 parameters

### Build Signatures ###
1. To generate the database one has to first compile Signatures
2. cmake -DCMAKE_INSTALL_PREFIX=/home/<username>/.local -DUSER_LIBRARY_PATH=/home/jhineman/.local/lib .
3. make install
4. At this point you should be able to execute database part of the tutorial
at shaunharker.github.io/DSGRN/ for example
    $ ~/DSGRN$ which mpiexec
    /home/<username>/.local/bin/mpiexec
    $ ~/DSGRN$ mpiexec -np 5 ./software/Signatures/bin/Signatures networks/2D_Example_C.txt ./2D_Example_C.db
5. At this point you can also execute sqlite exploration of the database. If we want ot use the sqlite3
we have installed, use ~/.local/bin/sqlite3

## Using binaries and Conda (Draft) ##

1. Install Anaconda
2. Create a Conda environment (say 2.7) and Conda install relevant binaries from conda-forge
3. Procede as above, will likely need to pass library/include information to cmake