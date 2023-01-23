#target.symbol DataFormatsEgammaTrackReco
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsEgammaTrackReco SHARED 
  src/ConversionTrack.cc
)

set_target_properties(DataFormatsEgammaTrackReco PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsEgammaTrackReco)

install( TARGETS DataFormatsEgammaTrackReco DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsEgammaTrackReco PUBLIC
ROOT::Core
DataFormatsCaloRecHit
DataFormatsCommon
DataFormatsEgammaReco
DataFormatsTrackCandidate
DataFormatsTrackReco
DataFormatsTrackingRecHit
)

cms_rootdict(DataFormatsEgammaTrackReco src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsEgammaTrackReco)
