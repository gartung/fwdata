#target.symbol DataFormatsTrackerCommon
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsTrackerCommon SHARED 
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

cms_rootdict(DataFormatsTrackerCommon src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsTrackerCommon)
