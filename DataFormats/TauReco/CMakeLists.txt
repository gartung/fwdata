#target.symbol DataFormatsTauReco
include_directories(${CMAKE_SOURCE_DIR}
)






add_library(DataFormatsTauReco SHARED 
  src/BaseTau.cc
  src/BaseTauTagInfo.cc
  src/PFRecoTauChargedHadron.cc
  src/PFTau.cc
  src/PFTau3ProngSummary.cc
  src/PFTauDecayMode.cc
  src/PFTauTagInfo.cc
  src/PFTauTransverseImpactParameter.cc
  src/RecoTauPiZero.cc
)

set_target_properties(DataFormatsTauReco PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsTauReco)

install( TARGETS DataFormatsTauReco DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsTauReco PUBLIC
ROOT::Core
DataFormatsCandidate
DataFormatsCommon
DataFormatsJetReco
DataFormatsMath
DataFormatsParticleFlowCandidate
DataFormatsRecoCandidate
DataFormatsTrackReco
)

cms_rootdict(DataFormatsTauReco src/classes_hlt.h src/classes_def_hlt.xml)
add_rootdict_rules(DataFormatsTauReco)
