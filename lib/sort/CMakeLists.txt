
# define code files
set(fstsort_SRCS
    sort/openmphelper.cpp
	sort/sort_int.cpp
	sort/sort_logical.cpp
)

# declare fst library
add_library(fstsort STATIC
    ${fstsort_SRCS}
)

# add zstd and lz4 compression libraries
target_link_libraries(fstsort)

# exported include directories
target_include_directories(fstsort PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
)
