#target.symbol DataFormatsMuonReco
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${CLHEP_INCLUDE_DIR}
${EIGEN_INCLUDE_DIR}/eigen3
${FMT_INCLUDE_DIR}
${GSL_INCLUDE_DIR}
${HEPMC_INCLUDE_DIR}
${CMSMD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
${VDT_INCLUDE_DIR}
${XZ_INCLUDE_DIR}
/usr/include
)

cms_rootdict(DataFormatsMuonReco src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsMuonReco)

add_library(DataFormatsMuonReco SHARED ${DataFormatsMuonReco_EXTRA_SOURCES}
  src/CaloMuon.cc
  src/DYTInfo.cc
  src/Muon.cc
  src/MuonChamberMatch.cc
  src/MuonCocktails.cc
  src/MuonSelectors.cc
  src/MuonSimInfo.cc
  src/MuonTimeExtra.cc
)

set_target_properties(DataFormatsMuonReco PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsMuonReco)

install( TARGETS DataFormatsMuonReco DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsMuonReco PUBLIC
ROOT::Core
DataFormatsCSCRecHit
DataFormatsCommon
DataFormatsDTRecHit
DataFormatsGEMRecHit
DataFormatsRecoCandidate
DataFormatsTrackReco
DataFormatsVertexReco
ROOT::Core
ROOT::GenVector
ROOT::MathCore
ROOT::MathMore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
)

