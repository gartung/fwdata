#target.symbol DataFormatsL1TGlobal
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${EIGEN_INCLUDE_DIR}/eigen3
${FMT_INCLUDE_DIR}
${GSL_INCLUDE_DIR}
${MD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
/usr/include
)

cms_rootdict(DataFormatsL1TGlobal src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsL1TGlobal)

add_library(DataFormatsL1TGlobal SHARED ${DataFormatsL1TGlobal_EXTRA_SOURCES}
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

