#target.symbol DataFormatsL1CSCTrackFinder
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsL1CSCTrackFinder SHARED 
  src/CSCTFConstants.cc
  src/L1Track.cc
  src/L1TrackId.cc
  src/TrackStub.cc
)

set_target_properties(DataFormatsL1CSCTrackFinder PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsL1CSCTrackFinder)

install( TARGETS DataFormatsL1CSCTrackFinder DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsL1CSCTrackFinder PUBLIC
ROOT::Core
DataFormatsCSCDigi
DataFormatsCommon
DataFormatsDetId
DataFormatsL1GlobalMuonTrigger
DataFormatsMuonDetId
)

cms_rootdict(DataFormatsL1CSCTrackFinder src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsL1CSCTrackFinder)
