#target.symbol CondFormatsAlignment
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
/usr/include
)

cms_rootdict(CondFormatsAlignment src/classes.h src/classes_def.xml)

add_rootdict_rules(CondFormatsAlignment)

add_library(CondFormatsAlignment SHARED ${CondFormatsAlignment_EXTRA_SOURCES}
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
${Boost_SERIALIZATION_LIBRARY_RELEASE}
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
${NSL}
${RT}
)

