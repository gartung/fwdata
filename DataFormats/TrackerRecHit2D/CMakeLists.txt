#target.symbol DataFormatsTrackerRecHit2D
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${CLHEP_INCLUDE_DIR}
${EIGEN_INCLUDE_DIR}/eigen3
${FMT_INCLUDE_DIR}
${GSL_INCLUDE_DIR}
${CMSMD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
${VDT_INCLUDE_DIR}
/usr/include
)



add_library(DataFormatsTrackerRecHit2D SHARED 
  src/BaseTrackerRecHit.cc
  src/ClusterRemovalInfo.cc
  src/FastMatchedTrackerRecHit.cc
  src/FastProjectedTrackerRecHit.cc
  src/FastSingleTrackerRecHit.cc
  src/FastTrackerRecHit.cc
  src/MTDTrackingRecHit.cc
  src/ProjectedSiStripRecHit2D.cc
  src/SiPixelRecHit.cc
  src/SiPixelRecHitQuality.cc
  src/SiStripMatchedRecHit2D.cc
  src/SiStripRecHit1D.cc
  src/SiStripRecHit2D.cc
  src/SiTrackerMultiRecHit.cc
  src/TrackerSingleRecHit.cc
  src/TrackingRecHitLessFromGlobalPosition.cc
  src/VectorHit.cc
)

set_target_properties(DataFormatsTrackerRecHit2D PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsTrackerRecHit2D)

install( TARGETS DataFormatsTrackerRecHit2D DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsTrackerRecHit2D PUBLIC
ROOT::Core
CLHEP::CLHEP
DataFormatsCLHEP
DataFormatsCommon
DataFormatsFTLRecHit
DataFormatsGeometryVector
DataFormatsMath
DataFormatsPhase2TrackerCluster
DataFormatsPhase2TrackerDigi
DataFormatsTrackingRecHit
DataFormatsTrajectorySeed
DataFormatsTrajectoryState
FWCoreMessageLogger
FWCoreUtilities
GeometryCommonTopologies
ROOT::Core
ROOT::GenVector
ROOT::MathCore
ROOT::MathMore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
)

cms_rootdict(DataFormatsTrackerRecHit2D src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsTrackerRecHit2D)
