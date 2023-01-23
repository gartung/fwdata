#target.symbol DataFormatsHcalIsolatedTrack
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsHcalIsolatedTrack SHARED 
  src/EcalIsolatedParticleCandidate.cc
  src/HcalIsolatedTrackCandidate.cc
  src/IsolatedPixelTrackCandidate.cc
)

set_target_properties(DataFormatsHcalIsolatedTrack PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsHcalIsolatedTrack)

install( TARGETS DataFormatsHcalIsolatedTrack DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsHcalIsolatedTrack PUBLIC
ROOT::Core
DataFormatsCandidate
DataFormatsCommon
DataFormatsL1Trigger
DataFormatsMath
DataFormatsRecoCandidate
DataFormatsTrackReco
)

cms_rootdict(DataFormatsHcalIsolatedTrack src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsHcalIsolatedTrack)
