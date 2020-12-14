#target.symbol DataFormatsCaloTowers
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
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

cms_rootdict(DataFormatsCaloTowers src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsCaloTowers)

add_library(DataFormatsCaloTowers SHARED ${DataFormatsCaloTowers_EXTRA_SOURCES}
  src/CaloTower.cc
  src/CaloTowerDetId.cc
)

set_target_properties(DataFormatsCaloTowers PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsCaloTowers)

install( TARGETS DataFormatsCaloTowers DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsCaloTowers PUBLIC
ROOT::Core
DataFormatsCandidate
DataFormatsCommon
DataFormatsDetId
DataFormatsGeometryVector
DataFormatsHcalDetId
DataFormatsMath
FWCoreUtilities
)

