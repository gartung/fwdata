#target.symbol DataFormatsLuminosity
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsLuminosity SHARED 
  src/BeamCurrentInfo.cc
  src/LumiDetails.cc
  src/LumiInfo.cc
  src/LumiInfoRunHeader.cc
  src/LumiSummary.cc
  src/LumiSummaryRunHeader.cc
)

set_target_properties(DataFormatsLuminosity PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsLuminosity)

install( TARGETS DataFormatsLuminosity DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsLuminosity PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsMath
FWCoreUtilities
)

cms_rootdict(DataFormatsLuminosity src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsLuminosity)
