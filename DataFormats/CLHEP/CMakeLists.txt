#target.symbol DataFormatsCLHEP
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsCLHEP SHARED )

set_target_properties(DataFormatsCLHEP PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsCLHEP)

install( TARGETS DataFormatsCLHEP DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_include_directories(DataFormatsCLHEP PUBLIC ${CLHEP_INCLUDE_DIR})
target_link_libraries(DataFormatsCLHEP PUBLIC
ROOT::Core
CLHEP::CLHEP
DataFormatsMath
ROOT::Core
ROOT::GenVector
ROOT::MathCore
ROOT::MathMore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
)


cms_rootdict(DataFormatsCLHEP src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsCLHEP)
