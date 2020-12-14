#target.symbol DataFormatsScalers
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

cms_rootdict(DataFormatsScalers src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsScalers)

add_library(DataFormatsScalers SHARED ${DataFormatsScalers_EXTRA_SOURCES}
  src/BeamSpotOnline.cc
  src/DcsStatus.cc
  src/L1AcceptBunchCrossing.cc
  src/L1TriggerRates.cc
  src/L1TriggerScalers.cc
  src/Level1TriggerRates.cc
  src/Level1TriggerScalers.cc
  src/LumiScalers.cc
  src/TimeSpec.cc
)

set_target_properties(DataFormatsScalers PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsScalers)

install( TARGETS DataFormatsScalers DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsScalers PUBLIC
ROOT::Core
DataFormatsCommon
)

