#target.symbol DataFormatsSiPixelCluster
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

cms_rootdict(DataFormatsSiPixelCluster src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsSiPixelCluster)

add_library(DataFormatsSiPixelCluster SHARED ${DataFormatsSiPixelCluster_EXTRA_SOURCES}
  src/SiPixelCluster.cc
  src/SiPixelClusterShapeCache.cc
)

set_target_properties(DataFormatsSiPixelCluster PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsSiPixelCluster)

install( TARGETS DataFormatsSiPixelCluster DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsSiPixelCluster PUBLIC
ROOT::Core
DataFormatsCommon
)

