#target.symbol SimDataFormatsTrackingAnalysis
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(SimDataFormatsTrackingAnalysis SHARED 
  src/TrackingParticle.cc
  src/TrackingVertex.cc
)

set_target_properties(SimDataFormatsTrackingAnalysis PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS SimDataFormatsTrackingAnalysis)

install( TARGETS SimDataFormatsTrackingAnalysis DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(SimDataFormatsTrackingAnalysis PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsHepMCCandidate
DataFormatsMath
DataFormatsTrackReco
SimDataFormatsEncodedEventId
SimDataFormatsGeneratorProducts
SimDataFormatsTrack
SimDataFormatsVertex
)

cms_rootdict(SimDataFormatsTrackingAnalysis src/classes.h src/classes_def.xml)
add_rootdict_rules(SimDataFormatsTrackingAnalysis)
