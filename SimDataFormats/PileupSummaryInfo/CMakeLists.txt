#target.symbol SimDataFormatsPileupSummaryInfo
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(SimDataFormatsPileupSummaryInfo SHARED 
  src/PileupSummaryInfo.cc
)

set_target_properties(SimDataFormatsPileupSummaryInfo PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS SimDataFormatsPileupSummaryInfo)

install( TARGETS SimDataFormatsPileupSummaryInfo DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(SimDataFormatsPileupSummaryInfo PUBLIC
ROOT::Core
${HEPMC_HepMC_LIBRARY}
DataFormatsCommon
DataFormatsMath
DataFormatsProvenance
)

cms_rootdict(SimDataFormatsPileupSummaryInfo src/classes.h src/classes_def.xml)
add_rootdict_rules(SimDataFormatsPileupSummaryInfo)
