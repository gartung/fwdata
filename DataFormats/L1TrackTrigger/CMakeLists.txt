#target.symbol DataFormatsL1Trigger
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${EIGEN_INCLUDE_DIR}/eigen3
${FMT_INCLUDE_DIR}
${GSL_INCLUDE_DIR}
${CMSMD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
${HLS_INCLUDE_DIR}
/usr/include
)



add_library(DataFormatsL1TrackTrigger SHARED 
   src/TTCluster.cc
   src/TTDTC.cc
   src/TTTrack.cc
   src/TTTrack_TrackWord.cc
	)

set_target_properties(DataFormatsL1TrackTrigger PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsL1TrackTrigger)

install( TARGETS DataFormatsL1TrackTrigger DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsL1TrackTrigger PUBLIC
ROOT::Core
CLHEP::CLHEP
DataFormatsCommon
DataFormatsHcalDetId
FWCoreConcurrency
)

cms_rootdict(DataFormatsL1TrackTrigger src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsL1TrackTrigger)
