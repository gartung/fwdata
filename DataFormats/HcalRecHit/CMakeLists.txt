#target.symbol DataFormatsHcalRecHit
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

cms_rootdict(DataFormatsHcalRecHit src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsHcalRecHit)

add_library(DataFormatsHcalRecHit SHARED ${DataFormatsHcalRecHit_EXTRA_SOURCES}
  src/CastorRecHit.cc
  src/HBHEChannelInfo.cc
  src/HBHERecHit.cc
  src/HFPreRecHit.cc
  src/HFQIE10Info.cc
  src/HFRecHit.cc
  src/HORecHit.cc
  src/HcalCalibRecHit.cc
  src/HcalSourcePositionData.cc
  src/ZDCRecHit.cc
)

set_target_properties(DataFormatsHcalRecHit PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsHcalRecHit)

install( TARGETS DataFormatsHcalRecHit DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsHcalRecHit PUBLIC
ROOT::Core
DataFormatsCaloRecHit
DataFormatsCommon
DataFormatsHcalDetId
DataFormatsHcalDigi
)

