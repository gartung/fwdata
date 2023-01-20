#target.symbol DataFormatsCSCRecHit
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsCSCRecHit SHARED 
  src/CSCRangeMapAccessor.cc
  src/CSCRecHit2D.cc
  src/CSCSegment.cc
)

set_target_properties(DataFormatsCSCRecHit PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsCSCRecHit)

install( TARGETS DataFormatsCSCRecHit DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsCSCRecHit PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsMuonDetId
DataFormatsTrackingRecHit
)

cms_rootdict(DataFormatsCSCRecHit src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsCSCRecHit)
