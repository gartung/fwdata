#target.symbol DataFormatsEgammaCandidates
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${CLHEP_INCLUDE_DIR}
${EIGEN_INCLUDE_DIR}/eigen3
${FMT_INCLUDE_DIR}
${GSL_INCLUDE_DIR}
${HEPMC_INCLUDE_DIR}
${MD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
${VDT_INCLUDE_DIR}
${XZ_INCLUDE_DIR}
/usr/include
)

cms_rootdict(DataFormatsEgammaCandidates src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsEgammaCandidates)

add_library(DataFormatsEgammaCandidates SHARED ${DataFormatsEgammaCandidates_EXTRA_SOURCES}
  src/Conversion.cc
  src/Electron.cc
  src/GsfElectron.cc
  src/GsfElectronCore.cc
  src/Photon.cc
  src/SiStripElectron.cc
)

set_target_properties(DataFormatsEgammaCandidates PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsEgammaCandidates)

install( TARGETS DataFormatsEgammaCandidates DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsEgammaCandidates PUBLIC
ROOT::Core
CLHEP::CLHEP
DataFormatsCLHEP
DataFormatsCaloRecHit
DataFormatsCaloTowers
DataFormatsCandidate
DataFormatsCommon
DataFormatsEgammaReco
DataFormatsGeometryCommonDetAlgo
DataFormatsGsfTrackReco
DataFormatsMath
DataFormatsRecoCandidate
DataFormatsTrackReco
DataFormatsTrackerRecHit2D
DataFormatsTrackingRecHit
DataFormatsVertexReco
FWCoreMessageLogger
ROOT::Core
ROOT::GenVector
ROOT::MathCore
ROOT::MathMore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
)

