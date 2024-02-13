cmake_minimum_required(VERSION 3.18.4)

# set the project name and version
project(ChrestCompilerFlags VERSION 1.0)

# set the default compiler flags
add_library(chrestCompilerFlags INTERFACE)

# allow the options to be turned off
option(enforceChrestCompilerFlags "set to ON to enforce compiler warnings flags" OFF)
if (enforceChrestCompilerFlags)
    target_compile_options(chrestCompilerFlags INTERFACE $<$<COMPILE_LANGUAGE:C>:$<$<OR:$<C_COMPILER_ID:Clang>,$<C_COMPILER_ID:AppleClang>,$<C_COMPILER_ID:GNU>>: -Wall -Wextra -Wwrite-strings -Wno-strict-aliasing -Wno-unknown-pragmas -Wsign-compare -fstack-protector -fno-stack-check >>>)
    target_compile_options(chrestCompilerFlags INTERFACE $<$<COMPILE_LANGUAGE:CXX>:$<$<OR:$<CXX_COMPILER_ID:Clang>,$<CXX_COMPILER_ID:AppleClang>,$<CXX_COMPILER_ID:GNU>>: -Wall -Wextra -Wwrite-strings -Wno-strict-aliasing -Wno-unknown-pragmas -Wsign-compare -fstack-protector -fno-stack-check >>>)
    target_compile_options(chrestCompilerFlags INTERFACE $<$<COMPILE_LANGUAGE:CXX>:$<$<CXX_COMPILER_ID:GNU>: >>)
endif ()
