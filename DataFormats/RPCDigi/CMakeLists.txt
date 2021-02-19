#target.symbol DataFormatsRPCDigi
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

cms_rootdict(DataFormatsRPCDigi src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsRPCDigi)

add_library(DataFormatsRPCDigi SHARED ${DataFormatsRPCDigi_EXTRA_SOURCES}
  src/DataRecord.cc
  src/ErrorRCDM.cc
  src/ErrorRDDM.cc
  src/ErrorRDM.cc
  src/RPCAMCLinkCounters.cc
  src/RPCDigi.cc
  src/RPCDigiL1Link.cc
  src/RPCRawDataCounts.cc
  src/ReadoutError.cc
  src/RecordBX.cc
  src/RecordCD.cc
  src/RecordSLD.cc
)

set_target_properties(DataFormatsRPCDigi PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsRPCDigi)

install( TARGETS DataFormatsRPCDigi DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsRPCDigi PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsMuonDetId
)

