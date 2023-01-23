#target.symbol SimDataFormatsGEMDigiSimLink
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(SimDataFormatsGEMDigiSimLink SHARED 
  src/GEMDigiSimLink.cc
  src/ME0DigiSimLink.cc
)

set_target_properties(SimDataFormatsGEMDigiSimLink PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS SimDataFormatsGEMDigiSimLink)

install( TARGETS SimDataFormatsGEMDigiSimLink DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(SimDataFormatsGEMDigiSimLink PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsGeometryVector
SimDataFormatsEncodedEventId
)

cms_rootdict(SimDataFormatsGEMDigiSimLink src/classes.h src/classes_def.xml)
add_rootdict_rules(SimDataFormatsGEMDigiSimLink)
