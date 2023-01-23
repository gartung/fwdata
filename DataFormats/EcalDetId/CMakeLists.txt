#target.symbol DataFormatsEcalDetId
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsEcalDetId SHARED 
  src/EBDetId.cc
  src/EEDetId.cc
  src/ESDetId.cc
  src/EcalElectronicsId.cc
  src/EcalPnDiodeDetId.cc
  src/EcalScDetId.cc
  src/EcalTrigTowerDetId.cc
  src/EcalTriggerElectronicsId.cc
)

set_target_properties(DataFormatsEcalDetId PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsEcalDetId)

install( TARGETS DataFormatsEcalDetId DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsEcalDetId PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsDetId
FWCoreUtilities
)

cms_rootdict(DataFormatsEcalDetId src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsEcalDetId)
