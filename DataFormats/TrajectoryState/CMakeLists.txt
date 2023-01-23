#target.symbol DataFormatsTrajectoryState
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsTrajectoryState SHARED )

set_target_properties(DataFormatsTrajectoryState PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsTrajectoryState)

install( TARGETS DataFormatsTrajectoryState DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsTrajectoryState PUBLIC
ROOT::Core
DataFormatsGeometryVector
ROOT::Core
ROOT::MathCore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
)


cms_rootdict(DataFormatsTrajectoryState src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsTrajectoryState)
