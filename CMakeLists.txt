add_library(gfakluge SHARED src/gfakluge.hpp)
set_target_properties(gfakluge PROPERTIES LINKER_LANGUAGE CXX) 

# pliib wants openMP, even though we dont...
include(${CMAKE_ROOT}/Modules/FindOpenMP.cmake)

message(STATUS "Checking for homebrewed version")
if(${CMAKE_CXX_COMPILER_ID} STREQUAL "AppleClang")
    find_path(OMP_PATH omp.h PATHS /usr/local/Cellar/libomp/*/include)
    if(OMP_PATH-NOTFOUND)
        message(STATUS "No homebrewed version found")
    else()
        message(STATUS "Found OMP at ${OMP_PATH}")
    endif()
endif()

target_include_directories(gfakluge INTERFACE src src/tinyFA src/tinyFA/pliib ${OMP_PATH})

