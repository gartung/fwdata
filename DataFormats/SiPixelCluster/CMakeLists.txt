#target.symbol DataFormatsSiPixelCluster
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsSiPixelCluster SHARED 
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

cms_rootdict(DataFormatsSiPixelCluster src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsSiPixelCluster)
