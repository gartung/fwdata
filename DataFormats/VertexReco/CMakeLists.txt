#target.symbol DataFormatsVertexReco
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

cms_rootdict(DataFormatsVertexReco src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsVertexReco)

add_library(DataFormatsVertexReco SHARED ${DataFormatsVertexReco_EXTRA_SOURCES}
  src/Vertex.cc
)

set_target_properties(DataFormatsVertexReco PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsVertexReco)

install( TARGETS DataFormatsVertexReco DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsVertexReco PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsTrackReco
)

