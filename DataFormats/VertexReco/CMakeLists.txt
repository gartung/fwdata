#target.symbol DataFormatsVertexReco
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsVertexReco SHARED 
  src/Vertex.cc
)

set_target_properties(DataFormatsVertexReco PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsVertexReco)

install( TARGETS DataFormatsVertexReco DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsVertexReco PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsTrackReco
)

cms_rootdict(DataFormatsVertexReco src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsVertexReco)
