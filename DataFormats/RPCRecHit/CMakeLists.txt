#target.symbol DataFormatsRPCRecHit
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsRPCRecHit SHARED 
  src/RPCRecHit.cc
)

set_target_properties(DataFormatsRPCRecHit PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsRPCRecHit)

install( TARGETS DataFormatsRPCRecHit DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsRPCRecHit PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsMuonDetId
DataFormatsTrackingRecHit
)

cms_rootdict(DataFormatsRPCRecHit src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsRPCRecHit)
