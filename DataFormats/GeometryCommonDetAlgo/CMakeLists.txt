#target.symbol DataFormatsGeometryCommonDetAlgo
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${CLHEP_INCLUDE_DIR}
${EIGEN_INCLUDE_DIR}/eigen3
${FMT_INCLUDE_DIR}
${GSL_INCLUDE_DIR}
${MD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
/usr/include
)

cms_rootdict(DataFormatsGeometryCommonDetAlgo src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsGeometryCommonDetAlgo)

add_library(DataFormatsGeometryCommonDetAlgo SHARED ${DataFormatsGeometryCommonDetAlgo_EXTRA_SOURCES}
  src/AlignmentPositionError.cc
  src/PerpendicularBoundPlaneBuilder.cc
  src/TransverseBoundPlaneFactory.cc
)

set_target_properties(DataFormatsGeometryCommonDetAlgo PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsGeometryCommonDetAlgo)

install( TARGETS DataFormatsGeometryCommonDetAlgo DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsGeometryCommonDetAlgo PUBLIC
ROOT::Core
${CLHEP_LIBRARIES}
${CLHEP_MAIN_LIBRARY}
DataFormatsCLHEP
DataFormatsCommon
DataFormatsGeometrySurface
DataFormatsGeometryVector
DataFormatsMath
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

