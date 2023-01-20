#target.symbol DataFormatsL1CaloTrigger
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsL1CaloTrigger SHARED 
  src/L1CaloEmCand.cc
  src/L1CaloMipQuietRegion.cc
  src/L1CaloRegion.cc
  src/L1CaloRegionDetId.cc
)

set_target_properties(DataFormatsL1CaloTrigger PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsL1CaloTrigger)

install( TARGETS DataFormatsL1CaloTrigger DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsL1CaloTrigger PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsDetId
)

cms_rootdict(DataFormatsL1CaloTrigger src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsL1CaloTrigger)
