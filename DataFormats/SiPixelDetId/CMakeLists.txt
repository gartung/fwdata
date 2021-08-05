#target.symbol DataFormatsSiPixelDetId
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${FMT_INCLUDE_DIR}
${CMSMD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
/usr/include
)

cms_rootdict(DataFormatsSiPixelDetId src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsSiPixelDetId)

add_library(DataFormatsSiPixelDetId SHARED ${DataFormatsSiPixelDetId_EXTRA_SOURCES}
  src/ES_PixelFEDChannelCollectionMap.cc
  src/PXBDetId.cc
  src/PXFDetId.cc
  src/PixelBarrelNameUpgrade.cc
  src/PixelEndcapNameUpgrade.cc
  src/PixelModuleName.cc
)

set_target_properties(DataFormatsSiPixelDetId PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsSiPixelDetId)

install( TARGETS DataFormatsSiPixelDetId DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsSiPixelDetId PUBLIC
ROOT::Core
DataFormatsDetId
FWCoreMessageLogger
FWCoreUtilities
)

