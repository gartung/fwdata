#target.symbol SimDataFormatsTrackingAnalysis
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

cms_rootdict(SimDataFormatsTrackingAnalysis src/classes.h src/classes_def.xml)

add_rootdict_rules(SimDataFormatsTrackingAnalysis)

add_library(SimDataFormatsTrackingAnalysis SHARED ${SimDataFormatsTrackingAnalysis_EXTRA_SOURCES}
  src/TrackingParticle.cc
  src/TrackingVertex.cc
)

set_target_properties(SimDataFormatsTrackingAnalysis PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS SimDataFormatsTrackingAnalysis)

install( TARGETS SimDataFormatsTrackingAnalysis DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(SimDataFormatsTrackingAnalysis PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsHepMCCandidate
DataFormatsMath
DataFormatsTrackReco
SimDataFormatsEncodedEventId
SimDataFormatsGeneratorProducts
SimDataFormatsTrack
SimDataFormatsVertex
)

