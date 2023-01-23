#target.symbol DataFormatsTrackReco
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsTrackReco SHARED 
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

cms_rootdict(DataFormatsTrackReco src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsTrackReco)
