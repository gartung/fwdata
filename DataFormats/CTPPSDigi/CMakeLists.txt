#target.symbol DataFormatsCTPPSDigi
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${FMT_INCLUDE_DIR}
${MD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
/usr/include
)

cms_rootdict(DataFormatsCTPPSDigi src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsCTPPSDigi)

add_library(DataFormatsCTPPSDigi SHARED ${DataFormatsCTPPSDigi_EXTRA_SOURCES}
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

