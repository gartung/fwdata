#target.symbol DataFormatsProvenance
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsProvenance SHARED 
  src/BranchChildren.cc
  src/BranchDescription.cc
  src/BranchID.cc
  src/BranchIDListHelper.cc
  src/BranchKey.cc
  src/BranchType.cc
  src/CompactEventAuxiliaryVector.cc
  src/ESRecordAuxiliary.cc
  src/ElementID.cc
  src/EventAux.cc
  src/EventAuxiliary.cc
  src/EventEntryDescription.cc
  src/EventEntryInfo.cc
  src/EventID.cc
  src/EventRange.cc
  src/FileFormatVersion.cc
  src/FileID.cc
  src/FileIndex.cc
  src/Hash.cc
  src/History.cc
  src/IndexIntoFile.cc
  src/LuminosityBlockAux.cc
  src/LuminosityBlockAuxiliary.cc
  src/LuminosityBlockID.cc
  src/LuminosityBlockRange.cc
  src/MergeableRunProductMetadataBase.cc
  src/ModuleDescription.cc
  src/ParameterSetBlob.cc
  src/Parentage.cc
  src/ParentageRegistry.cc
  src/ProcessConfiguration.cc
  src/ProcessHistory.cc
  src/ProcessHistoryRegistry.cc
  src/ProductID.cc
  src/ProductIDToBranchID.cc
  src/ProductProvenance.cc
  src/ProductProvenanceLookup.cc
  src/ProductProvenanceRetriever.cc
  src/ProductRegistry.cc
  src/ProductResolverIndexHelper.cc
  src/Provenance.cc
  src/RunAux.cc
  src/RunAuxiliary.cc
  src/RunID.cc
  src/RunLumiEntryInfo.cc
  src/StableProvenance.cc
  src/StoredMergeableRunProductMetadata.cc
  src/StoredProcessBlockHelper.cc
  src/SubProcessParentageHelper.cc
  src/ThinnedAssociationsHelper.cc
  src/Timestamp.cc
  src/ViewTypeChecker.cc
)

set_target_properties(DataFormatsProvenance PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsProvenance)

install( TARGETS DataFormatsProvenance DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsProvenance PUBLIC
ROOT::Core
TBB::tbb
FWCoreReflection
FWCoreUtilities
ROOT::Core
ROOT::MathCore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
)

cms_rootdict(DataFormatsProvenance src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsProvenance)
