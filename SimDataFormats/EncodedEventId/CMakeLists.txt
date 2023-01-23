#target.symbol SimDataFormatsEncodedEventId
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(SimDataFormatsEncodedEventId SHARED 
  src/EncodedEventId.cc
)

set_target_properties(SimDataFormatsEncodedEventId PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS SimDataFormatsEncodedEventId)

install( TARGETS SimDataFormatsEncodedEventId DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(SimDataFormatsEncodedEventId PUBLIC
ROOT::Core
ROOT::Core
ROOT::MathCore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
${CRYPT}
${DL}
${RT}
)

cms_rootdict(SimDataFormatsEncodedEventId src/classes.h src/classes_def.xml)
add_rootdict_rules(SimDataFormatsEncodedEventId)
