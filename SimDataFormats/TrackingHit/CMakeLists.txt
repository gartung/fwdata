#target.symbol SimDataFormatsTrackingHit
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(SimDataFormatsTrackingHit SHARED 
  src/PSimHit.cc
  )

set_target_properties(SimDataFormatsTrackingHit PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS SimDataFormatsTrackingHit)

install( TARGETS SimDataFormatsTrackingHit DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(SimDataFormatsTrackingHit PUBLIC
DataFormatsCommon
DataFormatsGeometryVector
SimDataFormatsEncodedEventId
)

cms_rootdict(SimDataFormatsTrackingHit src/classes.h src/classes_def.xml)
add_rootdict_rules(SimDataFormatsTrackingHit)
