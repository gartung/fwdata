#target.symbol DataFormatsCommon
include_directories(${CMAKE_SOURCE_DIR}
)

add_library(DataFormatsCommon SHARED
  src/CommonExceptions.cc
  src/ConvertHandle.cc
  src/DataFrameContainer.cc
  src/DetSetVectorNew.cc
  src/EDProductGetter.cc
  src/ELseverityLevel.cc
  src/HandleBase.cc
  src/HandleExceptionFactory.cc
  src/MergeableCounter.cc
  src/MultiAssociation.cc
  src/OrphanHandleBase.cc
  src/ProductData.cc
  src/PtrVectorBase.cc
  src/RefCore.cc
  src/RefCoreStreamer.cc
  src/RefCoreWithIndex.cc
  src/RefHolder.cc
  src/ThinnedAssociation.cc
  src/ValidHandle.cc
  src/View.cc
  src/WrapperBase.cc
  src/setIsMergeable.cc
  src/traits.cc
)

set_target_properties(DataFormatsCommon PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsCommon)

install( TARGETS DataFormatsCommon DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsCommon PUBLIC
ROOT::Core
TBB::tbb
DataFormatsProvenance
FWCoreMessageLogger
FWCoreUtilities
${CRYPT}
${DL}
${RT}
)




cms_rootdict(DataFormatsCommon src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsCommon)
