#target.symbol DataFormatsPhase2TrackerCluster
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsPhase2TrackerCluster SHARED )

set_target_properties(DataFormatsPhase2TrackerCluster PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsPhase2TrackerCluster)

install( TARGETS DataFormatsPhase2TrackerCluster DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsPhase2TrackerCluster PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsPhase2TrackerDigi
ROOT::Core
)


cms_rootdict(DataFormatsPhase2TrackerCluster src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsPhase2TrackerCluster)
