#target.symbol DataFormatsTauReco
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

cms_rootdict(DataFormatsTauReco src/classes_1.h src/classes_def_1.xml)

cms_rootdict(DataFormatsTauReco src/classes_2.h src/classes_def_2.xml)

cms_rootdict(DataFormatsTauReco src/classes_3.h src/classes_def_3.xml)

cms_rootdict(DataFormatsTauReco src/classes_hlt.h src/classes_def_hlt.xml)

add_rootdict_rules(DataFormatsTauReco)

add_library(DataFormatsTauReco SHARED ${DataFormatsTauReco_EXTRA_SOURCES}
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

