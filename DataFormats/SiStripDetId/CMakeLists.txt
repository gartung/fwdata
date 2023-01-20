#target.symbol DataFormatsSiStripDetId
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsSiStripDetId SHARED 
  src/SiStripDetId.cc
)

set_target_properties(DataFormatsSiStripDetId PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsSiStripDetId)

install( TARGETS DataFormatsSiStripDetId DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsSiStripDetId PUBLIC
ROOT::Core
DataFormatsDetId
)

cms_rootdict(DataFormatsSiStripDetId src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsSiStripDetId)
