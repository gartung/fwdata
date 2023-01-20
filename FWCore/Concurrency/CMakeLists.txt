#target.symbol FWCoreConcurrency
include_directories(${CMAKE_SOURCE_DIR}
)

add_library(FWCoreConcurrency SHARED 
  src/SerialTaskQueue.cc
  src/SharedResourceNames.cc
  src/ThreadSafeOutputFileStream.cc
  src/ThreadsController.cc
  src/WaitingTaskList.cc
  src/WaitingTaskWithArenaHolder.cc
  src/setNThreads.cc
)

set_target_properties(FWCoreConcurrency PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

add_dependencies( ALL_LIBS FWCoreConcurrency)

install( TARGETS FWCoreConcurrency DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(FWCoreConcurrency PUBLIC
TBB::tbb
FWCoreUtilities
)

