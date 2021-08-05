#target.symbol DataFormatsTrajectorySeed
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${CLHEP_INCLUDE_DIR}
${EIGEN_INCLUDE_DIR}/eigen3
${FMT_INCLUDE_DIR}
${GSL_INCLUDE_DIR}
${CMSMD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
${VDT_INCLUDE_DIR}
/usr/include
)

cms_rootdict(DataFormatsTrajectorySeed src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsTrajectorySeed)

add_library(DataFormatsTrajectorySeed SHARED ${DataFormatsTrajectorySeed_EXTRA_SOURCES})

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


