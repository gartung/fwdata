#target.symbol DataFormatsHepMCCandidate
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${EIGEN_INCLUDE_DIR}/eigen3
${FMT_INCLUDE_DIR}
${GSL_INCLUDE_DIR}
${MD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
/usr/include
)

cms_rootdict(DataFormatsHepMCCandidate src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsHepMCCandidate)

add_library(DataFormatsHepMCCandidate SHARED ${DataFormatsHepMCCandidate_EXTRA_SOURCES}
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

