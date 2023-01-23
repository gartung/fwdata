#target.symbol SimDataFormatsJetMatching
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(SimDataFormatsJetMatching SHARED )

set_target_properties(SimDataFormatsJetMatching PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS SimDataFormatsJetMatching)

install( TARGETS SimDataFormatsJetMatching DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(SimDataFormatsJetMatching PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsHepMCCandidate
DataFormatsJetReco
)


cms_rootdict(SimDataFormatsJetMatching src/classes.h src/classes_def.xml)
add_rootdict_rules(SimDataFormatsJetMatching)
