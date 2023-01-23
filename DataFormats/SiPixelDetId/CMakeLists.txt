#target.symbol DataFormatsSiPixelDetId
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsSiPixelDetId SHARED 
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

cms_rootdict(DataFormatsSiPixelDetId src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsSiPixelDetId)
