#target.symbol DataFormatsBeamSpot
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
/usr/include
)

cms_rootdict(DataFormatsBeamSpot src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsBeamSpot)

add_library(DataFormatsBeamSpot SHARED ${DataFormatsBeamSpot_EXTRA_SOURCES}
  src/BeamSpot.cc
)

set_target_properties(DataFormatsBeamSpot PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsBeamSpot)

install( TARGETS DataFormatsBeamSpot DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsBeamSpot PUBLIC
ROOT::Core
CLHEP::CLHEP
DataFormatsCLHEP
DataFormatsCommon
DataFormatsMath
ROOT::Core
ROOT::GenVector
ROOT::MathCore
ROOT::MathMore
ROOT::Net
ROOT::RIO
ROOT::Smatrix
ROOT::Thread
ROOT::Tree
)

