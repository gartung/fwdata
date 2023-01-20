#target.symbol FWCoreReflection
include_directories(${CMAKE_SOURCE_DIR}
)

add_library(FWCoreReflection SHARED 
  src/BaseWithDict.cc
  src/DictionaryTools.cc
  src/FunctionWithDict.cc
  src/IterWithDict.cc
  src/MemberWithDict.cc
  src/ObjectWithDict.cc
  src/TypeWithDict.cc
)

set_target_properties(FWCoreReflection PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

add_dependencies( ALL_LIBS FWCoreReflection)

install( TARGETS FWCoreReflection DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(FWCoreReflection PUBLIC
FWCoreUtilities
ROOT::Core
ROOT::MathCore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
)

