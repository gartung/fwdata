#target.symbol DataFormatsCTPPSDetId
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsCTPPSDetId SHARED 
  src/CTPPSDetId.cc
  src/CTPPSDiamondDetId.cc
  src/CTPPSPixelDetId.cc
  src/TotemRPDetId.cc
  src/TotemTimingDetId.cc
)

set_target_properties(DataFormatsCTPPSDetId PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsCTPPSDetId)

install( TARGETS DataFormatsCTPPSDetId DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsCTPPSDetId PUBLIC
ROOT::Core
DataFormatsDetId
)

cms_rootdict(DataFormatsCTPPSDetId src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsCTPPSDetId)
