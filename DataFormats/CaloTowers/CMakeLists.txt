#target.symbol DataFormatsCaloTowers
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsCaloTowers SHARED 
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

cms_rootdict(DataFormatsCaloTowers src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsCaloTowers)
