#target.symbol DataFormatsProtonReco
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsProtonReco SHARED 
  src/ForwardProton.cc
)

set_target_properties(DataFormatsProtonReco PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsProtonReco)

install( TARGETS DataFormatsProtonReco DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsProtonReco PUBLIC
ROOT::Core
DataFormatsCTPPSReco
DataFormatsCommon
)

cms_rootdict(DataFormatsProtonReco src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsProtonReco)
