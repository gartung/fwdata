#target.symbol DataFormatsFTLRecHit
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
${VDT_INCLUDE_DIR}
/usr/include
)

cms_rootdict(DataFormatsFTLRecHit src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsFTLRecHit)

add_library(DataFormatsFTLRecHit SHARED ${DataFormatsFTLRecHit_EXTRA_SOURCES}
  src/FTLCluster.cc
  src/FTLRecHit.cc
  src/FTLTrackingRecHit.cc
  src/FTLUncalibratedRecHit.cc
)

set_target_properties(DataFormatsFTLRecHit PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsFTLRecHit)

install( TARGETS DataFormatsFTLRecHit DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsFTLRecHit PUBLIC
ROOT::Core
DataFormatsCaloRecHit
DataFormatsCommon
DataFormatsDetId
DataFormatsForwardDetId
DataFormatsTrackingRecHit
)

