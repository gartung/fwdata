#target.symbol DataFormatsEgammaReco
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



add_library(DataFormatsEgammaReco SHARED 
  src/BasicCluster.cc
  src/ClusterShape.cc
  src/EgammaTrigger.cc
  src/ElectronSeed.cc
  src/HFEMClusterShape.cc
  src/PreshowerCluster.cc
  src/PreshowerClusterShape.cc
  src/SuperCluster.cc
)

set_target_properties(DataFormatsEgammaReco PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsEgammaReco)

install( TARGETS DataFormatsEgammaReco DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsEgammaReco PUBLIC
ROOT::Core
CLHEP::CLHEP
DataFormatsCLHEP
DataFormatsCaloRecHit
DataFormatsCommon
DataFormatsEcalRecHit
DataFormatsGeometryVector
DataFormatsMath
DataFormatsTrackReco
DataFormatsTrackingRecHit
DataFormatsTrajectorySeed
DataFormatsTrajectoryState
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

cms_rootdict(DataFormatsEgammaReco src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsEgammaReco)
