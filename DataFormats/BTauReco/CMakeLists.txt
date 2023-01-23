#target.symbol DataFormatsBTauReco
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsBTauReco SHARED 
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
CLHEP::CLHEP
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
${CRYPT}
${DL}
${RT}
)

cms_rootdict(DataFormatsBTauReco src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsBTauReco)
