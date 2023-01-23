#target.symbol DataFormatsHLTReco
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsHLTReco SHARED 
  src/HLTPerformanceInfo.cc
)

set_target_properties(DataFormatsHLTReco PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsHLTReco)

install( TARGETS DataFormatsHLTReco DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsHLTReco PUBLIC
ROOT::Core
DataFormatsCandidate
DataFormatsCommon
DataFormatsEgammaCandidates
DataFormatsHcalIsolatedTrack
DataFormatsJetReco
DataFormatsL1Trigger
DataFormatsMETReco
DataFormatsRecoCandidate
DataFormatsTauReco
FWCoreUtilities
)

cms_rootdict(DataFormatsHLTReco src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsHLTReco)
