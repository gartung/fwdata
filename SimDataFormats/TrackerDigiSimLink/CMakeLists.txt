#target.symbol SimDataFormatsTrackerDigiSimLink
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(SimDataFormatsTrackerDigiSimLink SHARED 
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
${CRYPT}
${DL}
${RT}
)

cms_rootdict(SimDataFormatsTrackerDigiSimLink src/classes.h src/classes_def.xml)
add_rootdict_rules(SimDataFormatsTrackerDigiSimLink)
