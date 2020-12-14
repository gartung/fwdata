#target.symbol DataFormatsHLTReco
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

cms_rootdict(DataFormatsHLTReco src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsHLTReco)

add_library(DataFormatsHLTReco SHARED ${DataFormatsHLTReco_EXTRA_SOURCES}
  src/HLTPerformanceInfo.cc
)

set_target_properties(DataFormatsHLTReco PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsHLTReco)

install( TARGETS DataFormatsHLTReco DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsHLTReco PUBLIC
ROOT::Core
DataFormatsCandidate
DataFormatsCommon
DataFormatsEgammaCandidates
DataFormatsHcalIsolatedTrack
DataFormatsJetReco
DataFormatsL1Trigger
DataFormatsMETReco
DataFormatsRecoCandidate
DataFormatsTauReco
FWCoreUtilities
)

