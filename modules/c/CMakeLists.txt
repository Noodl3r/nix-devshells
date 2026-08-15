cmake_minimum_required(VERSION 3.20)

project(MyProject VERSION 0.1.0 LANGUAGES C)

set(CMAKE_C_STANDARD 17)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_EXTENSIONS OFF)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

target_include_directories(myproject PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)

# Manually add source directories here.
# You otherwise will need to glob and those can be inconsistent.
add_executable(${PROJECT_NAME} src/main.c)

target_compile_options(${PROJECT_NAME} PRIVATE -Wall -Wextra -Wpedantic -O3)

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    target_compile_options(${PROJECT_NAME} PRIVATE -g3 -O0)
endif()
