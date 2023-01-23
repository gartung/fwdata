#target.symbol DataFormatsHepMCCandidate
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsHepMCCandidate SHARED 
  src/FlavorHistory.cc
  src/FlavorHistoryEvent.cc
  src/GenParticle.cc
  src/GenStatusFlags.cc
)

set_target_properties(DataFormatsHepMCCandidate PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsHepMCCandidate)

install( TARGETS DataFormatsHepMCCandidate DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsHepMCCandidate PUBLIC
ROOT::Core
DataFormatsCandidate
DataFormatsCommon
ROOT::Core
ROOT::Hist
ROOT::MathCore
ROOT::Matrix
ROOT::Net
ROOT::Physics
ROOT::RIO
ROOT::Thread
ROOT::Tree
)

cms_rootdict(DataFormatsHepMCCandidate src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsHepMCCandidate)
