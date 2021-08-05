#target.symbol DataFormatsCSCDigi
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
${VDT_INCLUDE_DIR}
/usr/include
)

cms_rootdict(DataFormatsCSCDigi src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsCSCDigi)

add_library(DataFormatsCSCDigi SHARED ${DataFormatsCSCDigi_EXTRA_SOURCES}
  src/CSCALCTDigi.cc
  src/CSCALCTPreTriggerDigi.cc
  src/CSCALCTStatusDigi.cc
  src/CSCCFEBStatusDigi.cc
  src/CSCCLCTDigi.cc
  src/CSCCLCTPreTriggerDigi.cc
  src/CSCComparatorDigi.cc
  src/CSCCorrelatedLCTDigi.cc
  src/CSCDCCFormatStatusDigi.cc
  src/CSCDCCStatusDigi.cc
  src/CSCDDUStatusDigi.cc
  src/CSCDMBStatusDigi.cc
  src/CSCRPCDigi.cc
  src/CSCStripDigi.cc
  src/CSCTMBStatusDigi.cc
  src/CSCWireDigi.cc
)

set_target_properties(DataFormatsCSCDigi PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsCSCDigi)

install( TARGETS DataFormatsCSCDigi DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsCSCDigi PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsGEMDigi
DataFormatsMuonDetId
)

