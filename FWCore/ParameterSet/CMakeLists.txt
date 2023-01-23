#target.symbol FWCoreParameterSet
include_directories(${CMAKE_SOURCE_DIR}
)

add_library(FWCoreParameterSet SHARED 
  src/ANDGroupDescription.cc
  src/AllowedLabelsDescription.cc
  src/AllowedLabelsDescriptionBase.cc
  src/ConfigurationDescriptions.cc
  src/DocFormatHelper.cc
  src/EmptyGroupDescription.cc
  src/Entry.cc
  src/FillDescriptionFromPSet.cc
  src/IfExistsDescription.cc
  src/IllegalParameters.cc
  src/ORGroupDescription.cc
  src/ParameterDescription.cc
  src/ParameterDescriptionBase.cc
  src/ParameterDescriptionCases.cc
  src/ParameterDescriptionNode.cc
  src/ParameterSet.cc
  src/ParameterSetConverter.cc
  src/ParameterSetDescription.cc
  src/ParameterSetDescriptionFillerBase.cc
  src/ParameterSetDescriptionFillerPluginFactory.cc
  src/ParameterSetDescriptionTraits.cc
  src/ParameterSetEntry.cc
  src/ParameterSwitchBase.cc
  src/ParameterWildcard.cc
  src/ParameterWildcardBase.cc
  src/ProcessDesc.cc
  src/Registry.cc
  src/ThreadsInfo.cc
  src/VParameterSetEntry.cc
  src/XORGroupDescription.cc
  src/defaultModuleLabel.cc
  src/types.cc
  src/validateTopLevelParameterSets.cc
)

set_target_properties(FWCoreParameterSet PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

add_dependencies( ALL_LIBS FWCoreParameterSet)

install( TARGETS FWCoreParameterSet DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(FWCoreParameterSet PUBLIC
TBB::tbb
Boost::filesystem
Boost::system
DataFormatsProvenance
FWCoreMessageLogger
FWCorePluginManager
FWCoreUtilities
${CRYPT}
${DL}
${RT}
)

