#target.symbol DataFormatsL1TCalorimeter
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsL1TCalorimeter SHARED 
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

cms_rootdict(DataFormatsL1TCalorimeter src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsL1TCalorimeter)
