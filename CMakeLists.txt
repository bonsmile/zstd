cmake_minimum_required( VERSION 3.19.0 )

project(zstd LANGUAGES C VERSION 1.5.7)

set(CMAKE_THREAD_PREFER_PTHREAD TRUE)
set(THREADS_PREFER_PTHREAD_FLAG TRUE)
find_package(Threads REQUIRED)

add_library(zstd STATIC
	zstd.h
	zstd.c
)

target_link_libraries(zstd Threads::Threads)

if (CMAKE_CXX_COMPILER_ID STREQUAL "Clang")
	target_compile_options(${PROJECT_NAME} PRIVATE "-Wno-unused-function")
endif()
