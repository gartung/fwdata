#target.symbol DataFormatsGeometrySurface
include_directories(${CMAKE_SOURCE_DIR}
)



add_library(DataFormatsGeometrySurface SHARED 
  src/BoundCylinder.cc
  src/BoundDisk.cc
  src/BoundPlane.cc
  src/BoundSpan.cc
  src/BoundSurface.cc
  src/BoundingBox.cc
  src/Bounds.cc
  src/Cone.cc
  src/Cylinder.cc
  src/DiskSectorBounds.cc
  src/GeneralNSurfaceDelimitedBounds.cc
  src/LocalError.cc
  src/Plane.cc
  src/RectangularPlaneBounds.cc
  src/SimpleCylinderBounds.cc
  src/SimpleDiskBounds.cc
  src/TkRotation.cc
  src/TrapezoidalPlaneBounds.cc
)

set_target_properties(DataFormatsGeometrySurface PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS DataFormatsGeometrySurface)

install( TARGETS DataFormatsGeometrySurface DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(DataFormatsGeometrySurface PUBLIC
ROOT::Core
DataFormatsGeometryVector
${CRYPT}
${DL}
${RT}
)

cms_rootdict(DataFormatsGeometrySurface src/classes.h src/classes_def.xml)
add_rootdict_rules(DataFormatsGeometrySurface)
