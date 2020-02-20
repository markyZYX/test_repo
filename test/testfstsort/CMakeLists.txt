
# define test files
set(testfstsort_SRCS
	SetThreads.cpp
	sort_int_test.cpp
	sort_logical_test.cpp
)

# create test executable
add_executable(testfstsort
    ${testfstsort_SRCS}
)

# include_directories(src ${gtest_SOURCE_DIR}/include ${gtest_SOURCE_DIR})
target_link_libraries(testfstsort fstsort gtest gtest_main)
add_test(testfstsort testfstsort)
