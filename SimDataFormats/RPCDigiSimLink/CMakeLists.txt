#target.symbol SimDataFormatsRPCDigiSimLink
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(SimDataFormatsRPCDigiSimLink SHARED 
  src/RPCDigiSimLink.cc
)

set_target_properties(SimDataFormatsRPCDigiSimLink PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS SimDataFormatsRPCDigiSimLink)

install( TARGETS SimDataFormatsRPCDigiSimLink DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(SimDataFormatsRPCDigiSimLink PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsGeometryVector
SimDataFormatsEncodedEventId
${CRYPT}
${DL}
${RT}
)

cms_rootdict(SimDataFormatsRPCDigiSimLink src/classes.h src/classes_def.xml)
add_rootdict_rules(SimDataFormatsRPCDigiSimLink)
