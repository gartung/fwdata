#target.symbol SimDataFormatsDigiSimLinks
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(SimDataFormatsDigiSimLinks SHARED 
  src/DTDigiSimLink.cc
)

set_target_properties(SimDataFormatsDigiSimLinks PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS SimDataFormatsDigiSimLinks)

install( TARGETS SimDataFormatsDigiSimLinks DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(SimDataFormatsDigiSimLinks PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsMuonDetId
SimDataFormatsEncodedEventId
${CRYPT}
${DL}
${RT}
)

cms_rootdict(SimDataFormatsDigiSimLinks src/classes.h src/classes_def.xml)
add_rootdict_rules(SimDataFormatsDigiSimLinks)
