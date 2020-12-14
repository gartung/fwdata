#target.symbol DataFormatsParticleFlowReco
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

cms_rootdict(DataFormatsParticleFlowReco src/classes_1.h src/classes_def_1.xml)

cms_rootdict(DataFormatsParticleFlowReco src/classes_2.h src/classes_def_2.xml)

add_rootdict_rules(DataFormatsParticleFlowReco)

add_library(DataFormatsParticleFlowReco SHARED ${DataFormatsParticleFlowReco_EXTRA_SOURCES}
  src/GsfPFRecTrack.cc
  src/HGCalMultiCluster.cc
  src/PFBlock.cc
  src/PFBlockElement.cc
  src/PFBlockElementBrem.cc
  src/PFBlockElementCluster.cc
  src/PFBlockElementGsfTrack.cc
  src/PFBlockElementSuperCluster.cc
  src/PFBlockElementTrack.cc
  src/PFCluster.cc
  src/PFConversion.cc
  src/PFDisplacedVertex.cc
  src/PFDisplacedVertexCandidate.cc
  src/PFDisplacedVertexSeed.cc
  src/PFLayer.cc
  src/PFRecHit.cc
  src/PFRecHitFraction.cc
  src/PFRecTrack.cc
  src/PFSimParticle.cc
  src/PFSuperCluster.cc
  src/PFTrack.cc
  src/PFTrajectoryPoint.cc
  src/PreId.cc
  src/RecoPFClusterRefCandidate.cc
)

set_target_properties(DataFormatsParticleFlowReco PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsParticleFlowReco)

install( TARGETS DataFormatsParticleFlowReco DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsParticleFlowReco PUBLIC
ROOT::Core
${CLHEP_LIBRARIES}
${CLHEP_MAIN_LIBRARY}
DataFormatsCLHEP
DataFormatsCaloRecHit
DataFormatsCandidate
DataFormatsCommon
DataFormatsDetId
DataFormatsEgammaCandidates
DataFormatsEgammaReco
DataFormatsGeometryVector
DataFormatsGsfTrackReco
DataFormatsMath
DataFormatsMuonReco
DataFormatsTrackReco
DataFormatsTrackingRecHit
DataFormatsTrajectorySeed
DataFormatsTrajectoryState
DataFormatsVertexReco
FWCoreMessageLogger
FWCoreUtilities
GeometryCaloGeometry
ROOT::Core
ROOT::GenVector
ROOT::MathCore
ROOT::MathMore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
)

