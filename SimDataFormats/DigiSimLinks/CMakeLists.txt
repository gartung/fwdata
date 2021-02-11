#target.symbol SimDataFormatsDigiSimLinks
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${FMT_INCLUDE_DIR}
${MD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
/usr/include
)

cms_rootdict(SimDataFormatsDigiSimLinks src/classes.h src/classes_def.xml)

add_rootdict_rules(SimDataFormatsDigiSimLinks)

add_library(SimDataFormatsDigiSimLinks SHARED ${SimDataFormatsDigiSimLinks_EXTRA_SOURCES}
  src/DTDigiSimLink.cc
)

set_target_properties(SimDataFormatsDigiSimLinks PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS SimDataFormatsDigiSimLinks)

install( TARGETS SimDataFormatsDigiSimLinks DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(SimDataFormatsDigiSimLinks PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsMuonDetId
SimDataFormatsEncodedEventId
crypt
dl
nsl-2.26
rt
)

