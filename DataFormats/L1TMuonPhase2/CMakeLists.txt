#target.symbol DataFormatsL1TMuonPhase2
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${CLHEP_INCLUDE_DIR}
${EIGEN_INCLUDE_DIR}/eigen3
${FMT_INCLUDE_DIR}
${GSL_INCLUDE_DIR}
${CMSMD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
${VDT_INCLUDE_DIR}
/usr/include
)

cms_rootdict(DataFormatsL1TMuonPhase2 src/classes.h src/classes_def.xml)

add_rootdict_rules(DataFormatsL1TMuonPhse2)

add_library(DataFormatsL1TMuon SHARED ${DataFormatsL1TMuonPhase2_EXTRA_SOURCES}
)

set_target_properties(DataFormatsL1TMuonPhase2 PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsL1TMuonPhase2)

install( TARGETS DataFormatsL1TMuonPhase2 DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsL1TMuonPhase2 PUBLIC
ROOT::Core
DataFormatsCSCDigi
DataFormatsCandidate
DataFormatsCommon
DataFormatsGEMDigi
DataFormatsMuonDetId
ROOT::Core
)

