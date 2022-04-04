#target.symbol DataFormatsGEMDigi
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

cms_rootdict(DataFormatsGEMDigi src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsGEMDigi)

add_library(DataFormatsGEMDigi SHARED ${DataFormatsGEMDigi_EXTRA_SOURCES}
  src/AMC13Event.cc
  src/AMCdata.cc
  src/GEMAMC.cc
  src/GEMAMC13.cc
  src/GEMCoPadDigi.cc
  src/GEMDigi.cc
  src/GEMPadDigi.cc
  src/GEMPadDigiCluster.cc
  src/GEMVFAT.cc
  src/GEMVfatStatusDigi.cc
  src/ME0Digi.cc
  src/ME0DigiPreReco.cc
  src/ME0PadDigi.cc
  src/ME0PadDigiCluster.cc
  src/ME0TriggerDigi.cc
  src/VFATdata.cc
)

set_target_properties(DataFormatsGEMDigi PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsGEMDigi)

install( TARGETS DataFormatsGEMDigi DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsGEMDigi PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsGEMRecHit
DataFormatsMuonDetId
)

