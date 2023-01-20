#target.symbol DataFormatsScouting
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsScouting SHARED )

set_target_properties(DataFormatsScouting PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsScouting)

install( TARGETS DataFormatsScouting DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsScouting PUBLIC
DataFormatsCommon
)

cms_rootdict(DataFormatsScouting src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsScouting)
