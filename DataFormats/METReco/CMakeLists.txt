#target.symbol DataFormatsMETReco
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

cms_rootdict(DataFormatsMETReco src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsMETReco)

add_library(DataFormatsMETReco SHARED ${DataFormatsMETReco_EXTRA_SOURCES}
  src/BeamHaloSummary.cc
  src/CSCHaloData.cc
  src/CaloMET.cc
  src/EcalHaloData.cc
  src/GenMET.cc
  src/GlobalHaloData.cc
  src/HaloClusterCandidateECAL.cc
  src/HaloClusterCandidateHCAL.cc
  src/HcalCaloFlagTool.cc
  src/HcalHaloData.cc
  src/HcalNoiseHPD.cc
  src/HcalNoiseRBX.cc
  src/HcalNoiseSummary.cc
  src/MET.cc
  src/PFClusterMET.cc
  src/PFMET.cc
  src/PUSubMETData.cc
  src/PhiWedge.cc
  src/SigInputObj.cc
)

set_target_properties(DataFormatsMETReco PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsMETReco)

install( TARGETS DataFormatsMETReco DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsMETReco PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsEcalRecHit
DataFormatsHcalRecHit
DataFormatsJetReco
DataFormatsRecoCandidate
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

