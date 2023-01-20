#target.symbol DataFormatsGeometryCommonDetAlgo
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsGeometryCommonDetAlgo SHARED 
  src/AlignmentPositionError.cc
  src/PerpendicularBoundPlaneBuilder.cc
  src/TransverseBoundPlaneFactory.cc
)

set_target_properties(DataFormatsGeometryCommonDetAlgo PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsGeometryCommonDetAlgo)

install( TARGETS DataFormatsGeometryCommonDetAlgo DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsGeometryCommonDetAlgo PUBLIC
ROOT::Core
CLHEP::CLHEP
DataFormatsCLHEP
DataFormatsCommon
DataFormatsGeometrySurface
DataFormatsGeometryVector
DataFormatsMath
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

cms_rootdict(DataFormatsGeometryCommonDetAlgo src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsGeometryCommonDetAlgo)
