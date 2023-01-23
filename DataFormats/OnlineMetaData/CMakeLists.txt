#target.symbol DataFormatsOnlineMetaData
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsOnlineMetaData SHARED 
  src/CTPPSRecord.cc
  src/DCSRecord.cc
  src/OnlineLuminosityRecord.cc
)

set_target_properties(DataFormatsOnlineMetaData PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsOnlineMetaData)

install( TARGETS DataFormatsOnlineMetaData DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsOnlineMetaData PUBLIC
ROOT::Core
DataFormatsCommon
)

cms_rootdict(DataFormatsOnlineMetaData src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsOnlineMetaData)
