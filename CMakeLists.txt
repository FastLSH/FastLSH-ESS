cmake_minimum_required(VERSION 3.2)
project(FastLSH)

# Include the GoogleTest directory
set(GTEST_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/lib/googletest/googletest)
# Add GoogleTest as a build subdirectory
add_subdirectory(lib/googletest)
# Include the GoogleTest header directory
include_directories(${GTEST_DIRECTORY}/include)

#import OpenMP
find_package(OpenMP)
if (OPENMP_FOUND)
    set (CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${OpenMP_C_FLAGS}")
    set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
endif()


#complie with openmp
SET(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fopenmp")


set(CMAKE_CXX_STANDARD 11)

set(SOURCE_FILES
        README.md tests/driver.cpp include/LSH.h src/LSH.cpp
        tests/unitTests/MetaTest.cpp tests/unitTests/MTTests/StdthreadTest.cpp
        tests/unitTests/MTTests/PthreadTest.cpp
        tests/unitTests/MTTests/OpenMPTest.cpp
        src/Normalizer.cpp tests/unitTests/SingleThreadTest.cpp
        include/otherClasses/FileLoader.h
        include/otherClasses/Computer.h tests/unitTests/ComputerTest.cpp include/otherClasses/ParameterHolder.h
        include/otherClasses/Generator.h src/Generator.cpp src/Computer/PthreadComputer.cpp tests/unitTests/GeneratorTest.cpp src/Computer/SingleThreadComputer.cpp src/Computer/OpenMPComputer.cpp src/Computer/StdThreadComputer.cpp src/FileLoader/LfsLoader.cpp src/FileLoader/FileLoader.cpp  tests/helper.cpp)

set(Paragen_FILES src/paragen.cpp)

add_executable(FastLSH ${SOURCE_FILES})
add_executable(paraGen ${Paragen_FILES})

target_link_libraries (FastLSH ${HDFS_LIBRARIES} gtest)

