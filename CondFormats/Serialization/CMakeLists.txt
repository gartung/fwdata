#target.symbol CondFormatsSerialization
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
)

add_library(CondFormatsSerialization SHARED ${CondFormatsSerialization_EXTRA_SOURCES}
  src/templateInstantiations.cc
)

set_target_properties(CondFormatsSerialization PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

add_dependencies( ALL_LIBS CondFormatsSerialization)

install( TARGETS CondFormatsSerialization DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(CondFormatsSerialization PUBLIC
${Boost_SERIALIZATION_LIBRARY_RELEASE}
)

