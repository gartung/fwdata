#target.symbol DataFormatsSiPixelDigi
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsSiPixelDigi SHARED 
  src/PixelDigiCollection.cc
  src/SiPixelCalibDigi.cc
  src/SiPixelCalibDigiError.cc
)

set_target_properties(DataFormatsSiPixelDigi PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsSiPixelDigi)

install( TARGETS DataFormatsSiPixelDigi DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsSiPixelDigi PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsSiPixelDetId
)

cms_rootdict(DataFormatsSiPixelDigi src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsSiPixelDigi)
