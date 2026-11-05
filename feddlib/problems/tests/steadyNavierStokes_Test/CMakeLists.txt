tribits_add_executable(
	steadyNavierStokes_Test
	SOURCES main.cpp
)

tribits_add_test(
	steadyNavierStokes_Test
	NAME steadyNavierStokes_Test
	ARGS
	NUM_MPI_PROCS 4
)

tribits_copy_files_to_binary_dir(data_steadyNavierStokes_Test
	SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}
	SOURCE_FILES parametersPrec.xml parametersProblem.xml parametersSolver.xml parametersTeko.xml parametersPrecBlock.xml
	DEST_DIR ${CMAKE_CURRENT_BINARY_DIR}
	DEST_FILES parametersPrec.xml parametersProblem.xml parametersSolver.xml parametersTeko.xml parametersPrecBlock.xml
	EXEDEPS steadyNavierStokes_Test
)

tribits_copy_files_to_binary_dir(mesh_steadyNavierStokes_Test
	SOURCE_DIR ${CMAKE_SOURCE_DIR}/meshes
	SOURCE_FILES benchmark_2DAdpt_h01.mesh
	DEST_DIR ${CMAKE_CURRENT_BINARY_DIR}
	DEST_FILES benchmark_2DAdpt_h01.mesh
	EXEDEPS steadyNavierStokes_Test
)
