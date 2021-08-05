#target.symbol FWCoreReflection
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${FMT_INCLUDE_DIR}
${CMSMD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${UUID_INCLUDE_DIR}
/usr/include
)

add_library(FWCoreReflection SHARED ${FWCoreReflection_EXTRA_SOURCES}
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

