#target.symbol DataFormatsTrackReco
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

cms_rootdict(DataFormatsTrackReco src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsTrackReco)

add_library(DataFormatsTrackReco SHARED ${DataFormatsTrackReco_EXTRA_SOURCES}
  src/DeDxData.cc
  src/HitPattern.cc
  src/SeedStopReason.cc
  src/Track.cc
  src/TrackBase.cc
  src/TrackExtra.cc
  src/TrackResiduals.cc
  src/fillCovariance.cc
  src/rootio_HitPattern.cc
)

set_target_properties(DataFormatsTrackReco PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsTrackReco)

install( TARGETS DataFormatsTrackReco DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsTrackReco PUBLIC
ROOT::Core
CLHEP::CLHEP
DataFormatsBeamSpot
DataFormatsCLHEP
DataFormatsCandidate
DataFormatsCommon
DataFormatsDetId
DataFormatsForwardDetId
DataFormatsGeometryVector
DataFormatsMath
DataFormatsMuonDetId
DataFormatsSiPixelCluster
DataFormatsSiPixelDetId
DataFormatsSiStripCluster
DataFormatsSiStripDetId
DataFormatsTrackCandidate
DataFormatsTrackerCommon
DataFormatsTrackingRecHit
DataFormatsTrajectorySeed
DataFormatsTrajectoryState
FWCoreUtilities
ROOT::Core
ROOT::GenVector
ROOT::MathCore
ROOT::MathMore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
)

