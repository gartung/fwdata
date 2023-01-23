#target.symbol DataFormatsSiStripCommon
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsSiStripCommon SHARED 
  src/SiStripConstants.cc
  src/SiStripDetKey.cc
  src/SiStripEnumsAndStrings.cc
  src/SiStripEventSummary.cc
  src/SiStripFecKey.cc
  src/SiStripFedKey.cc
  src/SiStripHistoTitle.cc
  src/SiStripKey.cc
  src/SiStripNullKey.cc
)

set_target_properties(DataFormatsSiStripCommon PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsSiStripCommon)

install( TARGETS DataFormatsSiStripCommon DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsSiStripCommon PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsSiStripDetId
FWCoreMessageLogger
)

cms_rootdict(DataFormatsSiStripCommon src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsSiStripCommon)
