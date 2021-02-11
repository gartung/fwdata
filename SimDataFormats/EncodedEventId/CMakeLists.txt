#target.symbol SimDataFormatsEncodedEventId
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
/usr/include
)

cms_rootdict(SimDataFormatsEncodedEventId src/classes.h src/classes_def.xml)

add_rootdict_rules(SimDataFormatsEncodedEventId)

add_library(SimDataFormatsEncodedEventId SHARED ${SimDataFormatsEncodedEventId_EXTRA_SOURCES}
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
crypt
dl
nsl-2.26
rt
)

