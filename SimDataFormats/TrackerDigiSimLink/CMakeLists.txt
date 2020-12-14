#target.symbol SimDataFormatsTrackerDigiSimLink
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${FMT_INCLUDE_DIR}
${MD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
/usr/include
)

cms_rootdict(SimDataFormatsTrackerDigiSimLink src/classes.h src/classes_def.xml)

add_rootdict_rules(SimDataFormatsTrackerDigiSimLink)

add_library(SimDataFormatsTrackerDigiSimLink SHARED ${SimDataFormatsTrackerDigiSimLink_EXTRA_SOURCES}
  src/PixelDigiSimLink.cc
  src/StripCompactDigiSimLinks.cc
  src/StripDigiSimLink.cc
)

set_target_properties(SimDataFormatsTrackerDigiSimLink PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS SimDataFormatsTrackerDigiSimLink)

install( TARGETS SimDataFormatsTrackerDigiSimLink DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(SimDataFormatsTrackerDigiSimLink PUBLIC
ROOT::Core
DataFormatsCommon
SimDataFormatsEncodedEventId
crypt
dl
nsl
rt
)

