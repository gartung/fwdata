#target.symbol SimDataFormatsTrack
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(SimDataFormatsTrack SHARED 
  src/CoreSimTrack.cc
  src/SimTrack.cc
)

set_target_properties(SimDataFormatsTrack PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS SimDataFormatsTrack)

install( TARGETS SimDataFormatsTrack DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(SimDataFormatsTrack PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsMath
SimDataFormatsEncodedEventId
)

cms_rootdict(SimDataFormatsTrack src/classes.h src/classes_def.xml)
add_rootdict_rules(SimDataFormatsTrack)
