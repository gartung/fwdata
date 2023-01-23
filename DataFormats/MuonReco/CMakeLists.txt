#target.symbol DataFormatsMuonReco
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsMuonReco SHARED 
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

cms_rootdict(DataFormatsMuonReco src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsMuonReco)
