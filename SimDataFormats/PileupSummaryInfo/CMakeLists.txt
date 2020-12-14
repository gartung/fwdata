#target.symbol SimDataFormatsPileupSummaryInfo
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${EIGEN_INCLUDE_DIR}/eigen3
${FMT_INCLUDE_DIR}
${GSL_INCLUDE_DIR}
${HEPMC_INCLUDE_DIR}
${MD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
/usr/include
)

cms_rootdict(SimDataFormatsPileupSummaryInfo src/classes.h src/classes_def.xml)

add_rootdict_rules(SimDataFormatsPileupSummaryInfo)

add_library(SimDataFormatsPileupSummaryInfo SHARED ${SimDataFormatsPileupSummaryInfo_EXTRA_SOURCES}
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

