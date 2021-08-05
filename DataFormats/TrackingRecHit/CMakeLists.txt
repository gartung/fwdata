#target.symbol DataFormatsTrackingRecHit
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${CLHEP_INCLUDE_DIR}
${EIGEN_INCLUDE_DIR}/eigen3
${FMT_INCLUDE_DIR}
${GSL_INCLUDE_DIR}
${MD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
${VDT_INCLUDE_DIR}
/usr/include
)

cms_rootdict(DataFormatsTrackingRecHit src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsTrackingRecHit)

add_library(DataFormatsTrackingRecHit SHARED ${DataFormatsTrackingRecHit_EXTRA_SOURCES}
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

