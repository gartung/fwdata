#target.symbol DataFormatsGEMRecHit
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsGEMRecHit SHARED 
  src/GEMCSCSegment.cc
  src/GEMRecHit.cc
  src/GEMSegment.cc
  src/ME0RecHit.cc
  src/ME0Segment.cc
)

set_target_properties(DataFormatsGEMRecHit PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsGEMRecHit)

install( TARGETS DataFormatsGEMRecHit DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsGEMRecHit PUBLIC
ROOT::Core
DataFormatsCSCRecHit
DataFormatsCommon
DataFormatsMuonDetId
DataFormatsTrackingRecHit
ROOT::Core
)

cms_rootdict(DataFormatsGEMRecHit src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsGEMRecHit)
