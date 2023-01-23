#target.symbol DataFormatsHGCRecHit
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsHGCRecHit SHARED 
  src/HGCRecHit.cc
  src/HGCUncalibratedRecHit.cc
)

set_target_properties(DataFormatsHGCRecHit PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsHGCRecHit)

install( TARGETS DataFormatsHGCRecHit DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsHGCRecHit PUBLIC
ROOT::Core
DataFormatsCaloRecHit
DataFormatsCommon
DataFormatsForwardDetId
DataFormatsHcalDetId
)

cms_rootdict(DataFormatsHGCRecHit src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsHGCRecHit)
