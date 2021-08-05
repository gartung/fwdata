#target.symbol DataFormatsRecoCandidate
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${CLHEP_INCLUDE_DIR}
${EIGEN_INCLUDE_DIR}/eigen3
${FMT_INCLUDE_DIR}
${GSL_INCLUDE_DIR}
${HEPMC_INCLUDE_DIR}
${CMSMD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
${VDT_INCLUDE_DIR}
${XZ_INCLUDE_DIR}
/usr/include
)

cms_rootdict(DataFormatsRecoCandidate src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsRecoCandidate)

add_library(DataFormatsRecoCandidate SHARED ${DataFormatsRecoCandidate_EXTRA_SOURCES}
  src/CaloRecHitCandidate.cc
  src/IsoDeposit.cc
  src/IsoDepositVetos.cc
  src/RecoCaloTowerCandidate.cc
  src/RecoCandidate.cc
  src/RecoChargedCandidate.cc
  src/RecoChargedRefCandidate.cc
  src/RecoEcalCandidate.cc
  src/RecoStandAloneMuonCandidate.cc
)

set_target_properties(DataFormatsRecoCandidate PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsRecoCandidate)

install( TARGETS DataFormatsRecoCandidate DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsRecoCandidate PUBLIC
ROOT::Core
CLHEP::CLHEP
DataFormatsCaloRecHit
DataFormatsCaloTowers
DataFormatsCandidate
DataFormatsCommon
DataFormatsEgammaReco
DataFormatsGsfTrackReco
DataFormatsHcalRecHit
DataFormatsTrackReco
SimDataFormatsTrackingAnalysis
)

