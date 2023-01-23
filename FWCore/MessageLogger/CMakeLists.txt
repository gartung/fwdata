#target.symbol FWCoreMessageLogger
include_directories(${CMAKE_SOURCE_DIR}
)

add_library(FWCoreMessageLogger SHARED 
  src/AbstractMLscribe.cc
  src/edm_MessageLogger.cc
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

target_include_directories(FWCoreMessageLogger PRIVATE ${TINYXML2_INCLUDE_DIR})
target_link_libraries(FWCoreMessageLogger PUBLIC
ROOT::Core
TBB::tbb
${TINYXML2_LIBRARY}
DataFormatsProvenance
FWCoreUtilities
fmt::fmt
${CRYPT}
${DL}
${RT}
)

