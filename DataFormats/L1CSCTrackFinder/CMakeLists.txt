#target.symbol DataFormatsL1CSCTrackFinder
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${CLHEP_INCLUDE_DIR}
${EIGEN_INCLUDE_DIR}/eigen3
${FMT_INCLUDE_DIR}
${GSL_INCLUDE_DIR}
${CMSMD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
${VDT_INCLUDE_DIR}
/usr/include
)

cms_rootdict(DataFormatsL1CSCTrackFinder src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsL1CSCTrackFinder)

add_library(DataFormatsL1CSCTrackFinder SHARED ${DataFormatsL1CSCTrackFinder_EXTRA_SOURCES}
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

