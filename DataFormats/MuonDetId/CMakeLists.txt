#target.symbol DataFormatsMuonDetId
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

cms_rootdict(DataFormatsMuonDetId src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsMuonDetId)

add_library(DataFormatsMuonDetId SHARED ${DataFormatsMuonDetId_EXTRA_SOURCES}
  src/CSCDetId.cc
  src/CSCIndexer.cc
  src/CSCTriggerNumbering.cc
  src/DTChamberId.cc
  src/DTLayerId.cc
  src/DTSectCollId.cc
  src/DTSuperLayerId.cc
  src/DTWireId.cc
  src/GEMDetId.cc
  src/ME0DetId.cc
  src/RPCCompDetId.cc
  src/RPCDetId.cc
)

set_target_properties(DataFormatsMuonDetId PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsMuonDetId)

install( TARGETS DataFormatsMuonDetId DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsMuonDetId PUBLIC
ROOT::Core
DataFormatsDetId
FWCoreUtilities
)

