#target.symbol DataFormatsGEMRecHit
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

cms_rootdict(DataFormatsGEMRecHit src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsGEMRecHit)

add_library(DataFormatsGEMRecHit SHARED ${DataFormatsGEMRecHit_EXTRA_SOURCES}
  src/GEMCSCSegment.cc
  src/GEMRecHit.cc
  src/GEMSegment.cc
  src/ME0RecHit.cc
  src/ME0Segment.cc
)

set_target_properties(DataFormatsGEMRecHit PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsGEMRecHit)

install( TARGETS DataFormatsGEMRecHit DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsGEMRecHit PUBLIC
ROOT::Core
DataFormatsCSCRecHit
DataFormatsCommon
DataFormatsMuonDetId
DataFormatsTrackingRecHit
ROOT::Core
)

