#target.symbol DataFormatsParticleFlowCandidate
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
