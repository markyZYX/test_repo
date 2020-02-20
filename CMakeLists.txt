
# minimum cmake version
cmake_minimum_required(VERSION 2.8)

# use at least C++ 11
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# generate position independent code
set(CMAKE_POSITION_INDEPENDENT_CODE ON)


# define fstlib project
project(fstsort)

# use OpenMP if available
find_package(OpenMP)
if (OPENMP_FOUND)
	set (CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${OpenMP_C_FLAGS}")
	set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
	set (CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} ${OpenMP_EXE_LINKER_FLAGS}")
else()
	message("No OpenMP detected, fstlib builds without OpenMP but needs it for optimal performance!")
endif()

# add googletest library: https://github.com/google/googletest
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
add_subdirectory(ext/gtest)
enable_testing(true)

# add the fst library components
add_subdirectory(lib/sort)

# add unit tests
add_subdirectory(test/testfstsort)
