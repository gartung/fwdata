#target.symbol DataFormatsCandidate
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsCandidate SHARED 
  src/Candidate.cc
  src/CompositeCandidate.cc
  src/CompositePtrCandidate.cc
  src/CompositeRefBaseCandidate.cc
  src/CompositeRefCandidate.cc
  src/LeafCandidate.cc
  src/LeafRefCandidateT.cc
  src/NamedCompositeCandidate.cc
  src/OverlapChecker.cc
  src/Particle.cc
  src/ShallowCloneCandidate.cc
  src/ShallowClonePtrCandidate.cc
  src/VertexCompositeCandidate.cc
  src/VertexCompositePtrCandidate.cc
)

set_target_properties(DataFormatsCandidate PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsCandidate)

install( TARGETS DataFormatsCandidate DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsCandidate PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsGeometryVector
DataFormatsMath
FWCoreUtilities
ROOT::Core
ROOT::GenVector
ROOT::MathCore
ROOT::MathMore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
)

cms_rootdict(DataFormatsCandidate src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsCandidate)
