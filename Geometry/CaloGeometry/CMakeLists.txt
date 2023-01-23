#target.symbol GeometryCaloGeometry
include_directories(${CMAKE_SOURCE_DIR}
)

add_library(GeometryCaloGeometry SHARED 
  src/CaloCellCrossing.cc
  src/CaloCellGeometry.cc
  src/CaloGenericDetId.cc
  src/CaloGeometry.cc
  src/CaloNumberingScheme.cc
  src/CaloSubdetectorGeometry.cc
  src/ES_CaloGeometry.cc
  src/ES_CaloSubdetectorGeometry.cc
  src/EcalTrapezoidParameters.cc
  src/FlatHexagon.cc
  src/FlatTrd.cc
  src/IdealObliquePrism.cc
  src/IdealZPrism.cc
  src/PreshowerStrip.cc
  src/TruncatedPyramid.cc
)

set_target_properties(GeometryCaloGeometry PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

add_dependencies( ALL_LIBS GeometryCaloGeometry)

install( TARGETS GeometryCaloGeometry DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(GeometryCaloGeometry PUBLIC
CLHEP::CLHEP
DataFormatsCaloTowers
DataFormatsDetId
DataFormatsEcalDetId
DataFormatsGeometryVector
DataFormatsHcalDetId
DataFormatsMath
FWCoreMessageLogger
FWCoreUtilities
)

