#target.symbol DataFormatsFTLRecHit
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsFTLRecHit SHARED 
  src/FTLCluster.cc
  src/FTLRecHit.cc
  src/FTLTrackingRecHit.cc
  src/FTLUncalibratedRecHit.cc
)

set_target_properties(DataFormatsFTLRecHit PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsFTLRecHit)

install( TARGETS DataFormatsFTLRecHit DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsFTLRecHit PUBLIC
ROOT::Core
DataFormatsCaloRecHit
DataFormatsCommon
DataFormatsDetId
DataFormatsForwardDetId
DataFormatsTrackingRecHit
)

cms_rootdict(DataFormatsFTLRecHit src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsFTLRecHit)
