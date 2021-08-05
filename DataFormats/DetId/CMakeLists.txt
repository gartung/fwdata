#target.symbol DataFormatsDetId
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${FMT_INCLUDE_DIR}
${CMSMD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
/usr/include
)

cms_rootdict(DataFormatsDetId src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsDetId)

add_library(DataFormatsDetId SHARED ${DataFormatsDetId_EXTRA_SOURCES}
  src/DetId.cc
)

set_target_properties(DataFormatsDetId PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsDetId)

install( TARGETS DataFormatsDetId DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsDetId PUBLIC
ROOT::Core
DataFormatsCommon
)

