#target.symbol DataFormatsBTauReco
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

cms_rootdict(DataFormatsBTauReco src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsBTauReco)

add_library(DataFormatsBTauReco SHARED ${DataFormatsBTauReco_EXTRA_SOURCES}
  src/IsolatedTauTagInfo.cc
  src/TaggingVariable.cc
  src/TauImpactParameterInfo.cc
  src/TauMassTagInfo.cc
  src/TemplatedSoftLeptonTagInfo.cc
  src/VertexTypes.cc
)

set_target_properties(DataFormatsBTauReco PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsBTauReco)

install( TARGETS DataFormatsBTauReco DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsBTauReco PUBLIC
ROOT::Core
${CLHEP_LIBRARIES}
${CLHEP_MAIN_LIBRARY}
DataFormatsCommon
DataFormatsJetReco
DataFormatsMath
DataFormatsParticleFlowCandidate
DataFormatsTrackReco
DataFormatsVertexReco
FWCoreUtilities
ROOT::Core
ROOT::GenVector
ROOT::MathCore
ROOT::MathMore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
crypt
dl
nsl
rt
)

