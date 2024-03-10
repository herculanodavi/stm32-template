cmake_minimum_required(VERSION 3.28)

set(CMAKE_TRY_COMPILE_TARGET_TYPE "STATIC_LIBRARY")

project(stm32-template
        VERSION 0.1.0
        LANGUAGES ASM C CXX)

add_executable(example "")

target_sources(example 
        PRIVATE
        src/main.cpp
)