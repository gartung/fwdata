#target.symbol CondFormatsAlignment
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(CondFormatsAlignment SHARED 
  src/DetectorGlobalPosition.cc
  src/T_EventSetup_Alignment.cc
  src/T_EventSetup_AlignmentError.cc
  src/T_EventSetup_AlignmentErrorExtended.cc
  src/T_EventSetup_AlignmentSurfaceDeformation.cc
  src/T_EventSetup_SurveyErrors.cc
)

set_target_properties(CondFormatsAlignment PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS CondFormatsAlignment)

install( TARGETS CondFormatsAlignment DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(CondFormatsAlignment PUBLIC
ROOT::Core
CLHEP::CLHEP
Boost::serialization
CondFormatsSerialization
DataFormatsCLHEP
DataFormatsDetId
DataFormatsEcalDetId
DataFormatsGeometrySurface
DataFormatsGeometryVector
DataFormatsL1GlobalTrigger
DataFormatsMath
DataFormatsProvenance
FWCoreUtilities
ROOT::Core
ROOT::GenVector
ROOT::MathCore
ROOT::MathMore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
${CRYPT}
${DL}
${RT}
)

cms_rootdict(CondFormatsAlignment src/classes.h src/classes_def.xml)
add_rootdict_rules(CondFormatsAlignment)
