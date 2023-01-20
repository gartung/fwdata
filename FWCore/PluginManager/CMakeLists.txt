#target.symbol FWCorePluginManager
include_directories(${CMAKE_SOURCE_DIR}
)

add_library(FWCorePluginManager SHARED 
  src/CacheParser.cc
  src/PluginCapabilities.cc
  src/PluginFactoryBase.cc
  src/PluginFactoryManager.cc
  src/PluginManager.cc
  src/PresenceFactory.cc
  src/ProblemTracker.cc
  src/SharedLibrary.cc
  src/standard.cc
)

set_target_properties(FWCorePluginManager PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

add_dependencies( ALL_LIBS FWCorePluginManager)

install( TARGETS FWCorePluginManager DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(FWCorePluginManager PUBLIC
TBB::tbb
FWCoreUtilities
ROOT::Core
ROOT::MathCore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
${CRYPT}
${DL}
${RT}
stdc++fs
)

