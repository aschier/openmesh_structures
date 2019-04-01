cmake_minimum_required(VERSION 2.8.10)
project(openmesh_structures)
include(CMakePackageConfigHelpers)

find_package(OpenMesh REQUIRED)

add_library(openmesh_structures INTERFACE)

target_compile_definitions(openmesh_structures INTERFACE -D_USE_MATH_DEFINES)
target_link_libraries(openmesh_structures INTERFACE ${OPENMESH_LIBRARIES})
target_include_directories(openmesh_structures INTERFACE
	$<INSTALL_INTERFACE:include>
	$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
	${OPENMESH_INCLUDE_DIR}
)


configure_package_config_file(openmesh_structuresConfig.cmake.in ${CMAKE_CURRENT_BINARY_DIR}/openmesh_structuresConfig.cmake INSTALL_DESTINATION ${CMAKE_INSTALL_PREFIX})
install(TARGETS openmesh_structures EXPORT openmesh_structures-targets)

install(EXPORT openmesh_structures-targets FILE openmesh_structuresTargets.cmake DESTINATION ${CMAKE_INSTALL_PREFIX})
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/openmesh_structuresConfig.cmake DESTINATION ${CMAKE_INSTALL_PREFIX})
install(DIRECTORY ./ DESTINATION include FILES_MATCHING PATTERN "*.h" PATTERN ".git" EXCLUDE)
