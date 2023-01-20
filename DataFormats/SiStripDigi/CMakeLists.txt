#target.symbol DataFormatsSiStripDigi
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



add_library(DataFormatsSiStripDigi SHARED 
  src/SiStripDigi.cc
)

set_target_properties(DataFormatsSiStripDigi PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsSiStripDigi)

install( TARGETS DataFormatsSiStripDigi DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsSiStripDigi PUBLIC
ROOT::Core
DataFormatsCommon
)

cms_rootdict(DataFormatsSiStripDigi src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsSiStripDigi)
