#[[
    Abstractions and Models are NOT at WAR!
                                            - Cobwoy's Talisman
    But Abstractions don't care and Models can't understand!!
                                            - Lul, Practicality
 ]]
cmake_minimum_required(VERSION 3.4)

# This is the top level CMakeList file having single responsibility of
# generating enough context for entire Software (Engine + Application).

# First we specify the C++/C standard
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(CMAKE_C_STANDARD 17)

# Control where the static and shared libraries are built
# We would want a semi-packaging fashioned way where all bianries are together
# whilst accessible from IDE (local debugger for instance!).
set(REPOSITORYROOT "${CMAKE_CURRENT_SOURCE_DIR}")

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${REPOSITORYROOT}/cppGMS")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${REPOSITORYROOT}/cppGMS")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${REPOSITORYROOT}/cppGMS")

# Setting some properties
# For grouping Libraries in folder
set_property(GLOBAL PROPERTY USE_FOLDERS ON)

# Set project
project(cppGameMemorySystem VERSION 1.0)

#----------------------------------------------------------------------------#
# code
file(GLOB_RECURSE CPPFILES ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp)
# Shows the headerfile directory in project
file(GLOB_RECURSE HEADERFILES ${CMAKE_CURRENT_SOURCE_DIR}/src/*.h)

# Finally the runnable file!
add_executable(cppGMS ${CPPFILES} ${HEADERFILES})

# Setting some flags

# For complete list of Compiler IDs check output_required_files
# https://cmake.org/cmake/help/latest/variable/CMAKE_LANG_COMPILER_ID.html#variable:CMAKE_%3CLANG%3E_COMPILER_ID
if(CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-deprecated-enum-enum-conversion")
	set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Werror-implicit-function-declaration")
endif()


#[[
 *                                          /\
 *                                         / /
 *                                      /\| |
 *                                      | | |/\
 *                                      | | / /
 *                                      | `  /
 *                                      `\  (___
 *                                     _.->  ,-.-.
 *                                  _.'      |  \ \
 *                                 /    _____| 0 |0\
 *                                |    /`    `^-.\.-'`-._
 *                                |   |                  `-._
 *                                |   :                      `.
 *                                \    `._     `-.__         O.'
 *         _.--,                   \     `._     __.^--._O_..-'
 *        `---, `.                  `\     /` ` `
 *             `\ `,                  `\   |
 *              |   :                   ;  |
 *              /    `.              ___|__|___
 *             /       `.           (          )
 *            /    `---.:____...---' `--------`.
 *           /        (         `.      __      `.
 *          |          `---------' _   /  \       \
 *          |    .-.      _._     (_)  `--'        \
 *          |   (   )    /   \                       \
 *           \   `-'     \   /                       ;-._
 *            \           `-'           \           .'   `.
 *            /`.                  `\    `\     _.-'`-.    `.___
 *           |   `-._                `\    `\.-'       `-.   ,--`
 *            \      `--.___        ___`\    \           ||^\\
 *             `._        | ``----''     `.   `\         `'  `
 *                `--;     \  jgs          `.   `.
 *                   //^||^\\               //^||^\\
 *                   '  `'  `               '   '  `
 ]]
