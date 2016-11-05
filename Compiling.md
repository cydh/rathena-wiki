Unix
----

### Using configure & make

Configure and make are commands used commonly to configure, build and install Linux applications.

#### Configure

#### Make

`make server`

You should be now noticing that you have 3 new files: **char-server**, **map-server**, and **login-server**. Make install is not yet supported.

### Using cmake & make

[Cmake](http://www.vtk.org/Wiki/CMake) is a cross-plateform configure.

Start creating a new sub directory and move there

`  mkdir build`
`  cd build`

#### Building makefiles

Generate the make files by cmake

`  cmake -G"Unix Makefiles" -DINSTALL_TO_SOURCE=ON ..`

    -- The C compiler identification is GNU
    -- Check for working C compiler: /usr/bin/cc
    -- Check for working C compiler: /usr/bin/cc -- works
    -- Detecting C compiler ABI info
    -- Detecting C compiler ABI info - done
    -- Detecting system MYSQL
    -- Found MYSQL: /usr/lib/libmysqlclient.so (found version "5.5.48-MariaDB")
    -- Detecting system MYSQL - done
    -- Configuring for system MYSQL
    -- Configuring for system MYSQL - done
    -- Detecting system PCRE
    -- Found PCRE: /usr/lib/x86_64-linux-gnu/libpcre.so (found version "8.31")
    -- Detecting system PCRE - done
    -- Configuring for system PCRE
    -- Configuring for system PCRE - done
    -- Detecting system ZLIB
    -- Found ZLIB: /usr/lib/x86_64-linux-gnu/libz.so (found version "1.2.8")
    -- Detecting system ZLIB - done
    -- Configuring for system ZLIB
    -- Configuring for system ZLIB - done
    -- Creating svnversion.h
    -- Creating svnversion.h - done
    -- Creating target common_base
    -- Creating target common_base - done
    -- Creating target common
    -- Creating target common - done
    -- Creating target login-server
    -- Creating target login-server - done
    -- Creating target char-server
    -- Creating target char-server - done
    -- Creating target map-server
    -- Enabled PCRE code
    -- Creating target map-server - done
    -- Creating target mapcache
    -- Creating target mapcache - done

    -- Available targets:
    --      common_base
    --      common
    --      login-server
    --      char-server
    --      map-server
    --      mapcache
    -- Configuring done
    -- Generating done
    -- Build files have been written to: /home/*/ra/build

#### Compilation

Then compile

`  make install`

    Scanning dependencies of target common_base
    [  1%] Building C object src/common/CMakeFiles/common_base.dir/__/__/3rdparty/mt19937ar/mt19937ar.c.o
    [  1%] Building C object src/common/CMakeFiles/common_base.dir/core.c.o
    [  2%] Building C object src/common/CMakeFiles/common_base.dir/db.c.o
    [  3%] Building C object src/common/CMakeFiles/common_base.dir/des.c.o
    ...
    [ 98%] Building C object src/tool/CMakeFiles/mapcache.dir/__/common/grfio.c.o
    [ 99%] Building C object src/tool/CMakeFiles/mapcache.dir/__/common/utils.c.o
    [100%] Building C object src/tool/CMakeFiles/mapcache.dir/mapcache.c.o
    ...
    -- Installing: ~/rathena/./login-server
    -- Installing: ~/rathena/./char-server
    -- Installing: ~/rathena/./map-server
    -- Installing: ~/rathena/./mapcache

You'll see nice green output progression then finally login-server, map-server, char-server, in main folder

Windows
-------
