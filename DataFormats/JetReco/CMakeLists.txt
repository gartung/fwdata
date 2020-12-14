#target.symbol DataFormatsJetReco
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${CLHEP_INCLUDE_DIR}
${EIGEN_INCLUDE_DIR}/eigen3
${FMT_INCLUDE_DIR}
${GSL_INCLUDE_DIR}
${HEPMC_INCLUDE_DIR}
${MD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
${VDT_INCLUDE_DIR}
${XZ_INCLUDE_DIR}
/usr/include
)

cms_rootdict(DataFormatsJetReco src/classes_1.h src/classes_def_1.xml)

cms_rootdict(DataFormatsJetReco src/classes_2.h src/classes_def_2.xml)

cms_rootdict(DataFormatsJetReco src/classes_3.h src/classes_def_3.xml)

cms_rootdict(DataFormatsJetReco src/classes_4.h src/classes_def_4.xml)

add_rootdict_rules(DataFormatsJetReco)

add_library(DataFormatsJetReco SHARED ${DataFormatsJetReco_EXTRA_SOURCES}
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

