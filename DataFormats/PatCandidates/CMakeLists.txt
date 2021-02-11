#target.symbol DataFormatsPatCandidates
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

cms_rootdict(DataFormatsPatCandidates src/classes_objects.h src/classes_def_objects.xml)

cms_rootdict(DataFormatsPatCandidates src/classes_other.h src/classes_def_other.xml)

cms_rootdict(DataFormatsPatCandidates src/classes_trigger.h src/classes_def_trigger.xml)

cms_rootdict(DataFormatsPatCandidates src/classes_user.h src/classes_def_user.xml)

add_rootdict_rules(DataFormatsPatCandidates)

add_library(DataFormatsPatCandidates SHARED ${DataFormatsPatCandidates_EXTRA_SOURCES}
  src/CandKinResolution.cc
  src/CompositeCandidate.cc
  src/Conversion.cc
  src/CovarianceParameterization.cc
  src/Electron.cc
  src/EventHypothesis.cc
  src/Flags.cc
  src/GenericParticle.cc
  src/Jet.cc
  src/JetCorrFactors.cc
  src/MET.cc
  src/MHT.cc
  src/Muon.cc
  src/PATObject.cc
  src/PATTauDiscriminator.cc
  src/PFParticle.cc
  src/PackedCandidate.cc
  src/PackedGenParticle.cc
  src/PackedTriggerPrescales.cc
  src/ParametrizationHelper.cc
  src/Particle.cc
  src/Photon.cc
  src/ResolutionHelper.cc
  src/StringMap.cc
  src/Tau.cc
  src/TauJetCorrFactors.cc
  src/TauPFEssential.cc
  src/TauPFSpecific.cc
  src/TriggerAlgorithm.cc
  src/TriggerCondition.cc
  src/TriggerEvent.cc
  src/TriggerFilter.cc
  src/TriggerObject.cc
  src/TriggerObjectStandAlone.cc
  src/TriggerPath.cc
  src/UserData.cc
  src/VIDCutFlowResult.cc
  src/Vertexing.cc
  src/throwMissingLabel.cc
)

set_target_properties(DataFormatsPatCandidates PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsPatCandidates)

install( TARGETS DataFormatsPatCandidates DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsPatCandidates PUBLIC
ROOT::Core
${CLHEP_LIBRARIES}
${CLHEP_MAIN_LIBRARY}
DataFormatsBTauReco
DataFormatsCLHEP
DataFormatsCaloTowers
DataFormatsCandidate
DataFormatsCommon
DataFormatsEcalRecHit
DataFormatsEgammaCandidates
DataFormatsEgammaReco
DataFormatsGeometryCommonDetAlgo
DataFormatsGsfTrackReco
DataFormatsHLTReco
DataFormatsHepMCCandidate
DataFormatsJetReco
DataFormatsL1GlobalTrigger
DataFormatsL1Trigger
DataFormatsMETReco
DataFormatsMath
DataFormatsMuonReco
DataFormatsParticleFlowCandidate
DataFormatsProvenance
DataFormatsRecoCandidate
DataFormatsSiPixelDetId
DataFormatsSiStripDetId
DataFormatsTauReco
DataFormatsTrackReco
DataFormatsVertexReco
FWCoreCommon
FWCoreMessageLogger
FWCoreParameterSet
FWCoreReflection
FWCoreUtilities
ROOT::Core
ROOT::GenVector
ROOT::MathCore
ROOT::MathMore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
SimDataFormatsJetMatching
crypt
dl
nsl-2.26
rt
)

