#target.symbol DataFormatsL1Trigger
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
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

cms_rootdict(DataFormatsL1Trigger src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsL1Trigger)

add_library(DataFormatsL1Trigger SHARED ${DataFormatsL1Trigger_EXTRA_SOURCES}
  src/CaloSpare.cc
  src/EGamma.cc
  src/EtSum.cc
  src/EtSumHelper.cc
  src/HOTPDigiTwinMux.cc
  src/Jet.cc
  src/L1Candidate.cc
  src/L1DataEmulDigi.cc
  src/L1DataEmulRecord.cc
  src/L1DataEmulResult.cc
  src/L1EmParticle.cc
  src/L1EtMissParticle.cc
  src/L1HFRings.cc
  src/L1JetParticle.cc
  src/L1MonitorDigi.cc
  src/L1MuonParticle.cc
  src/L1ParticleMap.cc
  src/L1TriggerError.cc
  src/Muon.cc
  src/Tau.cc
)

set_target_properties(DataFormatsL1Trigger PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsL1Trigger)

install( TARGETS DataFormatsL1Trigger DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsL1Trigger PUBLIC
ROOT::Core
DataFormatsCandidate
DataFormatsCommon
DataFormatsHcalDetId
DataFormatsL1GlobalCaloTrigger
DataFormatsL1GlobalMuonTrigger
)

