#target.symbol DataFormatsL1DTTrackFinder
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

cms_rootdict(DataFormatsL1DTTrackFinder src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsL1DTTrackFinder)

add_library(DataFormatsL1DTTrackFinder SHARED ${DataFormatsL1DTTrackFinder_EXTRA_SOURCES}
  src/L1MuDTChambPhContainer.cc
  src/L1MuDTChambPhDigi.cc
  src/L1MuDTChambThContainer.cc
  src/L1MuDTChambThDigi.cc
  src/L1MuDTTrackCand.cc
  src/L1MuDTTrackContainer.cc
  src/L1Phase2MuDTPhContainer.cc
  src/L1Phase2MuDTPhDigi.cc
)

set_target_properties(DataFormatsL1DTTrackFinder PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsL1DTTrackFinder)

install( TARGETS DataFormatsL1DTTrackFinder DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsL1DTTrackFinder PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsL1GlobalMuonTrigger
)

