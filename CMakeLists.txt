# Sets the minimum version of CMake required to build the native
# library. You should either keep the default value or only pass a
# value of 3.4.0 or lower.

cmake_minimum_required(VERSION 3.4.1)

include_directories( zziplib-0.13.62/ 
                     lua-5.1.5/src/
                     luazip-1.2.6/src/
                     memorymapping/src/ )

# Creates and names a library, sets it as either STATIC
# or SHARED, and provides the relative paths to its source code.
# You can define multiple libraries, and CMake builds it for you.
# Gradle automatically packages shared libraries with your APK.

add_library( # Sets the name of the library.
             lua51

             # Sets the library as a shared library.
             SHARED

             # Provides a relative path to your source file(s).
             # Associated headers in the same location as their source
             # file are automatically included.
             lua-5.1.5/src/lapi.c
             lua-5.1.5/src/lauxlib.c
             lua-5.1.5/src/lbaselib.c
             lua-5.1.5/src/lcode.c
             lua-5.1.5/src/ldblib.c
             lua-5.1.5/src/ldebug.c
             lua-5.1.5/src/ldo.c
             lua-5.1.5/src/ldump.c
             lua-5.1.5/src/lfunc.c
             lua-5.1.5/src/lgc.c
             lua-5.1.5/src/linit.c
             lua-5.1.5/src/liolib.c
             lua-5.1.5/src/llex.c
             lua-5.1.5/src/lmathlib.c
             lua-5.1.5/src/lmem.c
             lua-5.1.5/src/loadlib.c
             lua-5.1.5/src/lobject.c
             lua-5.1.5/src/lopcodes.c
             lua-5.1.5/src/loslib.c
             lua-5.1.5/src/lparser.c
             lua-5.1.5/src/lstate.c
             lua-5.1.5/src/lstring.c
             lua-5.1.5/src/lstrlib.c
             lua-5.1.5/src/ltable.c
             lua-5.1.5/src/ltablib.c
             lua-5.1.5/src/ltm.c
             lua-5.1.5/src/lundump.c
             lua-5.1.5/src/lvm.c
             lua-5.1.5/src/lzio.c
             lua-5.1.5/src/print.c
             zziplib-0.13.62/zzip/dir.c
             zziplib-0.13.62/zzip/err.c
             zziplib-0.13.62/zzip/fetch.c
             zziplib-0.13.62/zzip/file.c
             zziplib-0.13.62/zzip/fseeko.c
             zziplib-0.13.62/zzip/info.c
             zziplib-0.13.62/zzip/memdisk.c
             zziplib-0.13.62/zzip/mmapped.c
             zziplib-0.13.62/zzip/plugin.c
             zziplib-0.13.62/zzip/stat.c
             zziplib-0.13.62/zzip/write.c
             zziplib-0.13.62/zzip/zip.c
             luazip-1.2.6/src/luazip.c
             android-compat/telldir.c
             memorymapping/src/fmemopen.c
             luajava-1.1/src/c/luajava.c )

# Searches for a specified prebuilt library and stores the path as a
# variable. Because system libraries are included in the search path by
# default, you only need to specify the name of the public NDK library
# you want to add. CMake verifies that the library exists before
# completing its build.

find_library( # Sets the name of the path variable.
              log-lib

              # Specifies the name of the NDK library that
              # you want CMake to locate.
              log )

find_library( zlib
              z )

# Specifies libraries CMake should link to your target library. You
# can link multiple libraries, such as libraries you define in the
# build script, prebuilt third-party libraries, or system libraries.

target_link_libraries( # Specifies the target library.
                       lua51

                       # Links the target library to the log library
                       # included in the NDK.
                       ${log-lib}
                       ${zlib} )
