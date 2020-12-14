#target.symbol DataFormatsTrackerCommon
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

cms_rootdict(DataFormatsTrackerCommon src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsTrackerCommon)

add_library(DataFormatsTrackerCommon SHARED ${DataFormatsTrackerCommon_EXTRA_SOURCES}
  src/ClusterSummary.cc
  src/ES_TrackerTopology.cc
  src/PixelBarrelName.cc
  src/PixelEndcapName.cc
  src/SiStripSubStructure.cc
  src/TrackerTopology.cc
)

set_target_properties(DataFormatsTrackerCommon PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsTrackerCommon)

install( TARGETS DataFormatsTrackerCommon DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsTrackerCommon PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsDetId
DataFormatsSiPixelCluster
DataFormatsSiPixelDetId
DataFormatsSiStripCluster
DataFormatsSiStripDetId
DataFormatsSiStripDigi
FWCoreMessageLogger
FWCoreUtilities
)

