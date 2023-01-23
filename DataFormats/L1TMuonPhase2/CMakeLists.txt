#target.symbol DataFormatsL1TMuonPhase2
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsL1TMuon SHARED 
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

cms_rootdict(DataFormatsL1TMuonPhase2 src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsL1TMuonPhse2)
