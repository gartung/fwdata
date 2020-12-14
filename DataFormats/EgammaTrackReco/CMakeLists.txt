#target.symbol DataFormatsEgammaTrackReco
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${CLHEP_INCLUDE_DIR}
${EIGEN_INCLUDE_DIR}/eigen3
${FMT_INCLUDE_DIR}
${GSL_INCLUDE_DIR}
${MD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
${VDT_INCLUDE_DIR}
/usr/include
)

cms_rootdict(DataFormatsEgammaTrackReco src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsEgammaTrackReco)

add_library(DataFormatsEgammaTrackReco SHARED ${DataFormatsEgammaTrackReco_EXTRA_SOURCES}
  src/ConversionTrack.cc
)

set_target_properties(DataFormatsEgammaTrackReco PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsEgammaTrackReco)

install( TARGETS DataFormatsEgammaTrackReco DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsEgammaTrackReco PUBLIC
ROOT::Core
DataFormatsCaloRecHit
DataFormatsCommon
DataFormatsEgammaReco
DataFormatsTrackCandidate
DataFormatsTrackReco
DataFormatsTrackingRecHit
)

