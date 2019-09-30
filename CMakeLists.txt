add_library(gfakluge STATIC src/gfakluge.hpp)
set_target_properties(gfakluge PROPERTIES LINKER_LANGUAGE CXX) 
target_include_directories(gfakluge INTERFACE src src/tinyFA src/tinyFA/pliib)
