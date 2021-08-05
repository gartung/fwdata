#target.symbol SimDataFormatsGEMDigiSimLink
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
/usr/include
)

cms_rootdict(SimDataFormatsGEMDigiSimLink src/classes.h src/classes_def.xml)

add_rootdict_rules(SimDataFormatsGEMDigiSimLink)

add_library(SimDataFormatsGEMDigiSimLink SHARED ${SimDataFormatsGEMDigiSimLink_EXTRA_SOURCES}
  src/GEMDigiSimLink.cc
  src/ME0DigiSimLink.cc
)

set_target_properties(SimDataFormatsGEMDigiSimLink PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS SimDataFormatsGEMDigiSimLink)

install( TARGETS SimDataFormatsGEMDigiSimLink DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(SimDataFormatsGEMDigiSimLink PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsGeometryVector
SimDataFormatsEncodedEventId
)

