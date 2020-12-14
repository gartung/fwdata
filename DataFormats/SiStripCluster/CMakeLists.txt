#target.symbol DataFormatsSiStripCluster
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

cms_rootdict(DataFormatsSiStripCluster src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsSiStripCluster)

add_library(DataFormatsSiStripCluster SHARED ${DataFormatsSiStripCluster_EXTRA_SOURCES}
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

