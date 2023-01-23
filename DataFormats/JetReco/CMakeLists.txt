#target.symbol DataFormatsJetReco
include_directories(${CMAKE_SOURCE_DIR}
)






add_library(DataFormatsJetReco SHARED 
  src/BasicJet.cc
  src/CaloJet.cc
  src/DiscretizedEnergyFlow.cc
  src/FFTJetProducerSummary.cc
  src/GenJet.cc
  src/GenericJet.cc
  src/JPTJet.cc
  src/Jet.cc
  src/JetExtendedAssociation.cc
  src/JetFloatAssociation.cc
  src/JetTracksAssociation.cc
  src/PFClusterJet.cc
  src/PFJet.cc
  src/PileupJetIdentifier.cc
  src/TrackJet.cc
)

set_target_properties(DataFormatsJetReco PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsJetReco)

install( TARGETS DataFormatsJetReco DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsJetReco PUBLIC
ROOT::Core
DataFormatsCaloTowers
DataFormatsCandidate
DataFormatsCommon
DataFormatsHepMCCandidate
DataFormatsParticleFlowCandidate
DataFormatsParticleFlowReco
DataFormatsTrackReco
FWCoreUtilities
)

cms_rootdict(DataFormatsJetReco src/classes_4.h src/classes_def_4.xml)
add_rootdict_rules(DataFormatsJetReco)
