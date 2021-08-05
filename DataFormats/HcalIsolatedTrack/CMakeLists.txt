#target.symbol DataFormatsHcalIsolatedTrack
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

cms_rootdict(DataFormatsHcalIsolatedTrack src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsHcalIsolatedTrack)

add_library(DataFormatsHcalIsolatedTrack SHARED ${DataFormatsHcalIsolatedTrack_EXTRA_SOURCES}
  src/EcalIsolatedParticleCandidate.cc
  src/HcalIsolatedTrackCandidate.cc
  src/IsolatedPixelTrackCandidate.cc
)

set_target_properties(DataFormatsHcalIsolatedTrack PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsHcalIsolatedTrack)

install( TARGETS DataFormatsHcalIsolatedTrack DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsHcalIsolatedTrack PUBLIC
ROOT::Core
DataFormatsCandidate
DataFormatsCommon
DataFormatsL1Trigger
DataFormatsMath
DataFormatsRecoCandidate
DataFormatsTrackReco
)

