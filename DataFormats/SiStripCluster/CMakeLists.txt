#target.symbol DataFormatsSiStripCluster
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsSiStripCluster SHARED 
  src/SiStripCluster.cc
)

set_target_properties(DataFormatsSiStripCluster PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsSiStripCluster)

install( TARGETS DataFormatsSiStripCluster DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsSiStripCluster PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsGeometryVector
DataFormatsSiStripDigi
DataFormatsTrajectoryState
ROOT::Core
ROOT::MathCore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
)

cms_rootdict(DataFormatsSiStripCluster src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsSiStripCluster)
