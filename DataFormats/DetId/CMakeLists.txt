#target.symbol DataFormatsDetId
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsDetId SHARED 
  src/DetId.cc
)

set_target_properties(DataFormatsDetId PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsDetId)

install( TARGETS DataFormatsDetId DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsDetId PUBLIC
ROOT::Core
DataFormatsCommon
)

cms_rootdict(DataFormatsDetId src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsDetId)
