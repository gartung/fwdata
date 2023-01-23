#target.symbol DataFormatsCastorReco
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsCastorReco SHARED 
  src/CastorCell.cc
  src/CastorCluster.cc
  src/CastorEgamma.cc
  src/CastorJet.cc
  src/CastorTower.cc
)

set_target_properties(DataFormatsCastorReco PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsCastorReco)

install( TARGETS DataFormatsCastorReco DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsCastorReco PUBLIC
ROOT::Core
DataFormatsCandidate
DataFormatsCommon
DataFormatsHcalRecHit
)

cms_rootdict(DataFormatsCastorReco src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsCastorReco)
