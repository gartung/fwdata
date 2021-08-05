#target.symbol FWCoreMessageLogger
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${FMT_INCLUDE_DIR}
${CMSMD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
/usr/include
)

cms_rootdict(FWCoreMessageLogger src/classes.h src/classes_def.xml)

add_rootdict_rules(FWCoreMessageLogger)

add_library(FWCoreMessageLogger SHARED ${FWCoreMessageLogger_EXTRA_SOURCES}
  src/AbstractMLscribe.cc
  src/ELextendedID.cc
  src/ELmap.cc
  src/ELseverityLevel.cc
  src/ErrorObj.cc
  src/ExceptionMessages.cc
  src/JobReport.cc
  src/MessageDrop.cc
  src/MessageLogger.cc
  src/MessageLoggerQ.cc
  src/MessageSender.cc
)

set_target_properties(FWCoreMessageLogger PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS FWCoreMessageLogger)

install( TARGETS FWCoreMessageLogger DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(FWCoreMessageLogger PUBLIC
ROOT::Core
${TBB_LIBRARIES}
${TINYXML2_LIBRARY}
DataFormatsProvenance
FWCoreUtilities
fmt::fmt
${CRYPT}
${DL}
${NSL}
${RT}
)

