#target.symbol DataFormatsTrackCandidate
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsTrackCandidate SHARED 
  src/TrajectoryStopReasons.cc
)

set_target_properties(DataFormatsTrackCandidate PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsTrackCandidate)

install( TARGETS DataFormatsTrackCandidate DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsTrackCandidate PUBLIC
ROOT::Core
CLHEP::CLHEP
DataFormatsCLHEP
DataFormatsCommon
DataFormatsGeometryVector
DataFormatsMath
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

cms_rootdict(DataFormatsTrackCandidate src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsTrackCandidate)
