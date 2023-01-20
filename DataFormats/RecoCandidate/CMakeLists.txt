#target.symbol DataFormatsRecoCandidate
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsRecoCandidate SHARED 
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

cms_rootdict(DataFormatsRecoCandidate src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsRecoCandidate)
