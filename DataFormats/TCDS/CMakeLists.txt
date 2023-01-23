#target.symbol DataFormatsTCDS
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsTCDS SHARED 
  src/BSTRecord.cc
  src/L1aInfo.cc
  src/TCDSRecord.cc
)

set_target_properties(DataFormatsTCDS PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsTCDS)

install( TARGETS DataFormatsTCDS DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsTCDS PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsFEDRawData
)

cms_rootdict(DataFormatsTCDS src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsTCDS)
