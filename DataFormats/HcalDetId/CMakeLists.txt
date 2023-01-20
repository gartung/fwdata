#target.symbol DataFormatsHcalDetId
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${FMT_INCLUDE_DIR}
${CMSMD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
/usr/include
)



add_library(DataFormatsHcalDetId SHARED 
  src/CastorElectronicsId.cc
  src/HcalCalibDetId.cc
  src/HcalCastorDetId.cc
  src/HcalDcsDetId.cc
  src/HcalDetId.cc
  src/HcalElectronicsId.cc
  src/HcalFrontEndId.cc
  src/HcalGenericDetId.cc
  src/HcalOtherDetId.cc
  src/HcalTestNumbering.cc
  src/HcalTrigTowerDetId.cc
  src/HcalZDCDetId.cc
)

set_target_properties(DataFormatsHcalDetId PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsHcalDetId)

install( TARGETS DataFormatsHcalDetId DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsHcalDetId PUBLIC
ROOT::Core
DataFormatsDetId
FWCoreUtilities
)

cms_rootdict(DataFormatsHcalDetId src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsHcalDetId)
