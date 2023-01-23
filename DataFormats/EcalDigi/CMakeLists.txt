#target.symbol DataFormatsEcalDigi
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsEcalDigi SHARED 
  src/EBDataFrame.cc
  src/EBSrFlag.cc
  src/EEDataFrame.cc
  src/EESrFlag.cc
  src/ESDataFrame.cc
  src/ESSample.cc
  src/EcalDataFrame.cc
  src/EcalEBTriggerPrimitiveDigi.cc
  src/EcalEBTriggerPrimitiveSample.cc
  src/EcalFEMSample.cc
  src/EcalLiteDTUSample.cc
  src/EcalMGPASample.cc
  src/EcalMatacqDigi.cc
  src/EcalPnDiodeDigi.cc
  src/EcalPseudoStripInputDigi.cc
  src/EcalPseudoStripInputSample.cc
  src/EcalSrFlag.cc
  src/EcalTimeDigi.cc
  src/EcalTrigPrimCompactColl.cc
  src/EcalTriggerPrimitiveDigi.cc
  src/EcalTriggerPrimitiveSample.cc
)

set_target_properties(DataFormatsEcalDigi PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsEcalDigi)

install( TARGETS DataFormatsEcalDigi DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsEcalDigi PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsEcalDetId
)

cms_rootdict(DataFormatsEcalDigi src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsEcalDigi)
