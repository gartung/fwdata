#target.symbol DataFormatsL1TCalorimeter
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

cms_rootdict(DataFormatsL1TCalorimeter src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsL1TCalorimeter)

add_library(DataFormatsL1TCalorimeter SHARED ${DataFormatsL1TCalorimeter_EXTRA_SOURCES}
  src/CaloCluster.cc
  src/CaloEmCand.cc
  src/CaloRegion.cc
  src/CaloStage1Cluster.cc
  src/CaloTower.cc
)

set_target_properties(DataFormatsL1TCalorimeter PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsL1TCalorimeter)

install( TARGETS DataFormatsL1TCalorimeter DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsL1TCalorimeter PUBLIC
ROOT::Core
DataFormatsL1Trigger
)

