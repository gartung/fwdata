#target.symbol FWCoreCommon
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(FWCoreCommon SHARED 
  src/EventBase.cc
  src/LuminosityBlockBase.cc
  src/OutputProcessBlockHelper.cc
  src/ProcessBlockHelperBase.cc
  src/ProcessBlockHelper.cc
  src/Provenance.cc
  src/RunBase.cc
  src/SubProcessBlockHelper.cc
  src/TriggerNames.cc
  src/TriggerResultsByName.cc
)

set_target_properties(FWCoreCommon PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS FWCoreCommon)

install( TARGETS FWCoreCommon DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(FWCoreCommon PUBLIC
ROOT::Core
DataFormatsCommon
DataFormatsProvenance
FWCoreParameterSet
FWCoreUtilities
)

cms_rootdict(FWCoreCommon src/classes.h src/classes_def.xml)
add_rootdict_rules(FWCoreCommon)
