#target.symbol DataFormatsCaloRecHit
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsCaloRecHit SHARED 
  src/CaloCluster.cc
  src/CaloID.cc
  src/CaloRecHit.cc
)

set_target_properties(DataFormatsCaloRecHit PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsCaloRecHit)

install( TARGETS DataFormatsCaloRecHit DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsCaloRecHit PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsDetId
DataFormatsMath
ROOT::Core
ROOT::GenVector
ROOT::MathCore
ROOT::MathMore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
)

cms_rootdict(DataFormatsCaloRecHit src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsCaloRecHit)
