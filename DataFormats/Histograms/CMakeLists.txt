#target.symbol DataFormatsHistorgrams
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsHistorgrams SHARED )

set_target_properties(DataFormatsHistorgrams PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsHistorgrams)

install( TARGETS DataFormatsHistorgrams DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsHistorgrams PUBLIC
ROOT::Hist
ROOT::Matrix
DataFormatsCommon
)

cms_rootdict(DataFormatsHistorgrams src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsHistorgrams)
