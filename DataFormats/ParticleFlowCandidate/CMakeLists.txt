#target.symbol DataFormatsParticleFlowCandidate
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsParticleFlowCandidate SHARED 
  src/IsolatedPFCandidate.cc
  src/PFCandidate.cc
  src/PFCandidateEGammaExtra.cc
  src/PFCandidateElectronExtra.cc
  src/PFCandidatePhotonExtra.cc
  src/PileUpPFCandidate.cc
)

set_target_properties(DataFormatsParticleFlowCandidate PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsParticleFlowCandidate)

install( TARGETS DataFormatsParticleFlowCandidate DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsParticleFlowCandidate PUBLIC
ROOT::Core
DataFormatsCandidate
DataFormatsCommon
DataFormatsEgammaCandidates
DataFormatsGsfTrackReco
DataFormatsMath
DataFormatsMuonReco
DataFormatsParticleFlowReco
DataFormatsTrackReco
FWCoreUtilities
ROOT::Core
ROOT::GenVector
ROOT::MathCore
ROOT::MathMore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
)

cms_rootdict(DataFormatsParticleFlowCandidate src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsParticleFlowCandidate)
