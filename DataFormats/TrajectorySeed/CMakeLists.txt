#target.symbol DataFormatsTrajectorySeed
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsTrajectorySeed SHARED )

set_target_properties(DataFormatsTrajectorySeed PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsTrajectorySeed)

install( TARGETS DataFormatsTrajectorySeed DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsTrajectorySeed PUBLIC
ROOT::Core
CLHEP::CLHEP
DataFormatsCLHEP
DataFormatsCommon
DataFormatsGeometryVector
DataFormatsMath
DataFormatsTrackingRecHit
DataFormatsTrajectoryState
FWCoreUtilities
ROOT::Core
ROOT::GenVector
ROOT::MathCore
ROOT::MathMore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
)


cms_rootdict(DataFormatsTrajectorySeed src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsTrajectorySeed)
