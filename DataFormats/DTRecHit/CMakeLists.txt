#target.symbol DataFormatsDTRecHit
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsDTRecHit SHARED 
  src/DTChamberRecSegment2D.cc
  src/DTEnums.cc
  src/DTRangeMapAccessor.cc
  src/DTRecHit1D.cc
  src/DTRecHit1DPair.cc
  src/DTRecSegment2D.cc
  src/DTRecSegment4D.cc
  src/DTSLRecCluster.cc
  src/DTSLRecSegment2D.cc
)

set_target_properties(DataFormatsDTRecHit PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsDTRecHit)

install( TARGETS DataFormatsDTRecHit DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsDTRecHit PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsDTDigi
DataFormatsGeometrySurface
DataFormatsGeometryVector
DataFormatsMuonDetId
DataFormatsTrackingRecHit
FWCoreUtilities
)

cms_rootdict(DataFormatsDTRecHit src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsDTRecHit)
