#target.symbol FWCoreParameterSet
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

add_library(FWCoreParameterSet SHARED ${FWCoreParameterSet_EXTRA_SOURCES}
  src/ANDGroupDescription.cc
  src/AllowedLabelsDescription.cc
  src/AllowedLabelsDescriptionBase.cc
  src/ConfigurationDescriptions.cc
  src/DocFormatHelper.cc
  src/EmptyGroupDescription.cc
  src/Entry.cc
  src/FileInPath.cc
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
${TBB_LIBRARIES}
${Boost_FILESYSTEM_LIBRARY_RELEASE}
${Boost_SYSTEM_LIBRARY_RELEASE}
DataFormatsProvenance
FWCoreMessageLogger
FWCorePluginManager
FWCoreUtilities
${CRYPT}
${DL}
${NSL}
${RT}
)

