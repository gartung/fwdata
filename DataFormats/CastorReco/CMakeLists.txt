#target.symbol DataFormatsCastorReco
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${EIGEN_INCLUDE_DIR}/eigen3
${FMT_INCLUDE_DIR}
${GSL_INCLUDE_DIR}
${CMSMD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
/usr/include
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
