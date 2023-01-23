#target.symbol DataFormatsCTPPSDigi
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsCTPPSDigi SHARED 
  src/CTPPSDiamondDigi.cc
  src/CTPPSPixelDataError.cc
  src/CTPPSPixelDigi.cc
  src/CTPPSPixelDigiCollection.cc
  src/TotemTimingDigi.cc
  src/TotemTimingEventInfo.cc
  src/TotemVFATStatus.cc
)

set_target_properties(DataFormatsCTPPSDigi PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsCTPPSDigi)

install( TARGETS DataFormatsCTPPSDigi DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsCTPPSDigi PUBLIC
ROOT::Core
DataFormatsCommon
)

cms_rootdict(DataFormatsCTPPSDigi src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsCTPPSDigi)
