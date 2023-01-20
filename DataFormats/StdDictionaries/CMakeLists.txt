#target.symbol DataFormatsStdDictionaries
include_directories(${CMAKE_SOURCE_DIR}
${ROOT_INCLUDE_DIR}
)






add_library(DataFormatsStdDictionaries SHARED )

set_target_properties(DataFormatsStdDictionaries PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsStdDictionaries)

install( TARGETS DataFormatsStdDictionaries DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsStdDictionaries PUBLIC
ROOT::Core
ROOT::Core
ROOT::MathCore
ROOT::Net
ROOT::RIO
ROOT::Thread
ROOT::Tree
)


cms_rootdict(DataFormatsStdDictionaries src/classes_vector.h src/classes_def_vector.xml)
add_rootdict_rules(DataFormatsStdDictionaries)
