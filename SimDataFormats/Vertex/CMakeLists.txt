#target.symbol SimDataFormatsVertex
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(SimDataFormatsVertex SHARED 
  src/CoreSimVertex.cc
  src/SimVertex.cc
)

set_target_properties(SimDataFormatsVertex PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS SimDataFormatsVertex)

install( TARGETS SimDataFormatsVertex DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(SimDataFormatsVertex PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsMath
SimDataFormatsEncodedEventId
)

cms_rootdict(SimDataFormatsVertex src/classes.h src/classes_def.xml)
add_rootdict_rules(SimDataFormatsVertex)
