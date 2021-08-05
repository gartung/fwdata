#target.symbol DataFormatsL1TMuon
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

cms_rootdict(DataFormatsL1TMuon src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsL1TMuon)

add_library(DataFormatsL1TMuon SHARED ${DataFormatsL1TMuon_EXTRA_SOURCES}
  src/BMTF/L1MuBMAddressArray.cc
  src/BMTF/L1MuBMSecProcId.cc
  src/BMTF/L1MuBMTrackAssParam.cc
  src/BMTF/L1MuBMTrackSegLoc.cc
  src/CPPFDigi.cc
  src/EMTFDaqOut.cc
  src/EMTFHit.cc
  src/EMTFRoad.cc
  src/EMTFTrack.cc
  src/L1MuBMTrack.cc
  src/L1MuBMTrackSegEta.cc
  src/L1MuBMTrackSegPhi.cc
  src/L1MuKBMTCombinedStub.cc
  src/L1MuKBMTrack.cc
  src/RegionalMuonCand.cc
)

set_target_properties(DataFormatsL1TMuon PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsL1TMuon)

install( TARGETS DataFormatsL1TMuon DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsL1TMuon PUBLIC
ROOT::Core
DataFormatsCSCDigi
DataFormatsCandidate
DataFormatsCommon
DataFormatsGEMDigi
DataFormatsMuonDetId
ROOT::Core
)

