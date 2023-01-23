#target.symbol DataFormatsTrackingRecHit
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsTrackingRecHit SHARED 
  src/InvalidTrackingRecHit.cc
  src/KfComponentsHolder.cc
  src/RecHit1D.cc
  src/RecHit2DLocalPos.cc
  src/TrackingRecHit.cc
)

set_target_properties(DataFormatsTrackingRecHit PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsTrackingRecHit)

install( TARGETS DataFormatsTrackingRecHit DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsTrackingRecHit PUBLIC
ROOT::Core
CLHEP::CLHEP
DataFormatsCLHEP
DataFormatsCommon
DataFormatsGeometryCommonDetAlgo
DataFormatsGeometrySurface
DataFormatsMath
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

cms_rootdict(DataFormatsTrackingRecHit src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsTrackingRecHit)
