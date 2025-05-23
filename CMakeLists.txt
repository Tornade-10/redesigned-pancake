# Profiling Option
option(ENABLE_PROFILING "Enable Tracy Profiling" OFF)
if (ENABLE_PROFILING)
    list(APPEND VCPKG_MANIFEST_FEATURES "profiling")
endif (ENABLE_PROFILING)

# GTest Option
option(ENABLE_GTESTS "Enable GTests" OFF)
if (ENABLE_GTESTS)
    list(APPEND VCPKG_MANIFEST_FEATURES "tests")
endif (ENABLE_GTESTS)

# Samples Option
option(ENABLE_SAMPLES "Enable Samples" OFF)
if (ENABLE_SAMPLES)
    list(APPEND VCPKG_MANIFEST_FEATURES "samples")
endif (ENABLE_SAMPLES)

cmake_minimum_required(VERSION 3.18)
project(redesigned-pancake)

# Set C++ standard
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if(ENABLE_PROFILING)
    find_package(Tracy CONFIG REQUIRED)
endif(ENABLE_PROFILING)

if(ENABLE_GTESTS)
    enable_testing()
    find_package(GTest CONFIG REQUIRED)
endif(ENABLE_GTESTS)

# Include all subdirectories
#add_subdirectory(crackitos_physics)
#add_subdirectory(external/crackitos_core/core)
#target_link_libraries(crackitos_physics PUBLIC crackitos_core)


add_executable(main main.cc)
