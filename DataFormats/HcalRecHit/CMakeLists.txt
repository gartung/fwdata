#target.symbol DataFormatsHcalRecHit
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsHcalRecHit SHARED 
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

cms_rootdict(DataFormatsHcalRecHit src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsHcalRecHit)
