#target.symbol DataFormatsL1TGlobal
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsL1TGlobal SHARED 
  src/GlobalAlgBlk.cc
  src/GlobalExtBlk.cc
  src/GlobalLogicParser.cc
  src/GlobalObject.cc
  src/GlobalObjectMap.cc
  src/GlobalObjectMapRecord.cc
)

set_target_properties(DataFormatsL1TGlobal PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsL1TGlobal)

install( TARGETS DataFormatsL1TGlobal DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsL1TGlobal PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsL1Trigger
)

cms_rootdict(DataFormatsL1TGlobal src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsL1TGlobal)
