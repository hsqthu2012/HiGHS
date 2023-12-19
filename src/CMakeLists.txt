# Define library.
# Outdated CMake approach: update in progress

set(basiclu_sources
  ipm/basiclu/basiclu_factorize.c
  ipm/basiclu/basiclu_solve_dense.c
  ipm/basiclu/lu_build_factors.c
  ipm/basiclu/lu_factorize_bump.c
  ipm/basiclu/lu_initialize.c
  ipm/basiclu/lu_markowitz.c
  ipm/basiclu/lu_setup_bump.c
  ipm/basiclu/lu_solve_sparse.c
  ipm/basiclu/basiclu_get_factors.c
  ipm/basiclu/basiclu_solve_for_update.c
  ipm/basiclu/lu_condest.c
  ipm/basiclu/lu_file.c
  ipm/basiclu/lu_internal.c
  ipm/basiclu/lu_matrix_norm.c
  ipm/basiclu/lu_singletons.c
  ipm/basiclu/lu_solve_symbolic.c
  ipm/basiclu/lu_update.c
  ipm/basiclu/basiclu_initialize.c
  ipm/basiclu/basiclu_solve_sparse.c
  ipm/basiclu/lu_pivot.c
  ipm/basiclu/lu_solve_dense.c
  ipm/basiclu/lu_solve_triangular.c
  ipm/basiclu/basiclu_object.c
  ipm/basiclu/basiclu_update.c
  ipm/basiclu/lu_dfs.c
  ipm/basiclu/lu_garbage_perm.c
  ipm/basiclu/lu_residual_test.c
  ipm/basiclu/lu_solve_for_update.c)

set(ipx_sources
  ipm/ipx/basiclu_kernel.cc
  ipm/ipx/basiclu_wrapper.cc
  ipm/ipx/basis.cc
  ipm/ipx/conjugate_residuals.cc
  ipm/ipx/control.cc
  ipm/ipx/crossover.cc
  ipm/ipx/diagonal_precond.cc
  ipm/ipx/forrest_tomlin.cc
  ipm/ipx/guess_basis.cc
  ipm/ipx/indexed_vector.cc
  ipm/ipx/info.cc
  ipm/ipx/ipm.cc
  ipm/ipx/ipx_c.cc
  ipm/ipx/iterate.cc
  ipm/ipx/kkt_solver.cc
  ipm/ipx/kkt_solver_basis.cc
  ipm/ipx/kkt_solver_diag.cc
  ipm/ipx/linear_operator.cc
  ipm/ipx/lp_solver.cc
  ipm/ipx/lu_factorization.cc
  ipm/ipx/lu_update.cc
  ipm/ipx/maxvolume.cc
  ipm/ipx/model.cc
  ipm/ipx/normal_matrix.cc
  ipm/ipx/sparse_matrix.cc
  ipm/ipx/sparse_utils.cc
  ipm/ipx/splitted_normal_matrix.cc
  ipm/ipx/starting_basis.cc
  ipm/ipx/symbolic_invert.cc
  ipm/ipx/timer.cc
  ipm/ipx/utils.cc)

# FAST_BUILD is set to on.
# At the moment used only for gradually updating the CMake targets build and
# install / export.
# Define library in modern CMake using target_*()
# No interfaces (apart from c); No ipx; New (short) ctest instances.
add_library(highs)

set_target_properties(highs PROPERTIES POSITION_INDEPENDENT_CODE ON)
target_compile_definitions(highs PUBLIC LIBHIGHS_STATIC_DEFINE)

target_sources(highs PRIVATE
  ../extern/filereaderlp/reader.cpp
  io/Filereader.cpp
  io/FilereaderLp.cpp
  io/FilereaderEms.cpp
  io/FilereaderMps.cpp
  io/HighsIO.cpp
  io/HMPSIO.cpp
  io/HMpsFF.cpp
  io/LoadOptions.cpp
  lp_data/Highs.cpp
  lp_data/HighsCallback.cpp
  lp_data/HighsDebug.cpp
  lp_data/HighsDeprecated.cpp
  lp_data/HighsInfo.cpp
  lp_data/HighsInfoDebug.cpp
  lp_data/HighsInterface.cpp
  lp_data/HighsLp.cpp
  lp_data/HighsLpUtils.cpp
  lp_data/HighsModelUtils.cpp
  lp_data/HighsRanging.cpp
  lp_data/HighsSolution.cpp
  lp_data/HighsSolutionDebug.cpp
  lp_data/HighsSolve.cpp
  lp_data/HighsStatus.cpp
  lp_data/HighsOptions.cpp
  presolve/ICrash.cpp
  presolve/ICrashUtil.cpp
  presolve/ICrashX.cpp
  mip/HighsMipSolver.cpp
  mip/HighsMipSolverData.cpp
  mip/HighsDomain.cpp
  mip/HighsDynamicRowMatrix.cpp
  mip/HighsLpRelaxation.cpp
  mip/HighsSeparation.cpp
  mip/HighsSeparator.cpp
  mip/HighsTableauSeparator.cpp
  mip/HighsModkSeparator.cpp
  mip/HighsPathSeparator.cpp
  mip/HighsCutGeneration.cpp
  mip/HighsSearch.cpp
  mip/HighsConflictPool.cpp
  mip/HighsCutPool.cpp
  mip/HighsCliqueTable.cpp
  mip/HighsGFkSolve.cpp
  mip/HighsTransformedLp.cpp
  mip/HighsLpAggregator.cpp
  mip/HighsDebugSol.cpp
  mip/HighsImplications.cpp
  mip/HighsPrimalHeuristics.cpp
  mip/HighsPseudocost.cpp
  mip/HighsNodeQueue.cpp
  mip/HighsObjectiveFunction.cpp
  mip/HighsRedcostFixing.cpp
  model/HighsHessian.cpp
  model/HighsHessianUtils.cpp
  model/HighsModel.cpp
  parallel/HighsTaskExecutor.cpp
  presolve/ICrashX.cpp
  presolve/HighsPostsolveStack.cpp
  presolve/HighsSymmetry.cpp
  presolve/HPresolve.cpp
  presolve/HPresolveAnalysis.cpp
  presolve/PresolveComponent.cpp
  qpsolver/a_asm.cpp
  qpsolver/a_quass.cpp
  qpsolver/basis.cpp
  qpsolver/quass.cpp
  qpsolver/ratiotest.cpp
  qpsolver/scaling.cpp
  qpsolver/perturbation.cpp
  simplex/HEkk.cpp
  simplex/HEkkControl.cpp
  simplex/HEkkDebug.cpp
  simplex/HEkkPrimal.cpp
  simplex/HEkkDual.cpp
  simplex/HEkkDualRHS.cpp
  simplex/HEkkDualRow.cpp
  simplex/HEkkDualMulti.cpp
  simplex/HEkkInterface.cpp
  simplex/HighsSimplexAnalysis.cpp
  simplex/HSimplex.cpp
  simplex/HSimplexDebug.cpp
  simplex/HSimplexNla.cpp
  simplex/HSimplexNlaDebug.cpp
  simplex/HSimplexNlaFreeze.cpp
  simplex/HSimplexNlaProductForm.cpp
  simplex/HSimplexReport.cpp
  test/KktCh2.cpp
  test/DevKkt.cpp
  util/HFactor.cpp
  util/HFactorDebug.cpp
  util/HFactorExtend.cpp
  util/HFactorRefactor.cpp
  util/HFactorUtils.cpp
  util/HighsHash.cpp
  util/HighsLinearSumBounds.cpp
  util/HighsMatrixPic.cpp
  util/HighsMatrixUtils.cpp
  util/HighsSort.cpp
  util/HighsSparseMatrix.cpp
  util/HighsUtils.cpp
  util/HSet.cpp
  util/HVectorBase.cpp
  util/stringutil.cpp
  interfaces/highs_c_api.cpp)

target_include_directories(highs PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
  $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}/highs>
)

target_include_directories(highs PRIVATE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/interfaces>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/io>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/ipm>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/ipm/ipx>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/ipm/basiclu>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/lp_data>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/mip>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/model>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/parallel>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/presolve>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/qpsolver>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/simplex>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/util>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/test>
)

target_include_directories(highs PRIVATE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/../extern/>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/../extern/filereader>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/../extern/pdqsort>
)

# target_compile_options(highs PRIVATE "-Wall")
# target_compile_options(highs PRIVATE "-Wunused")
target_sources(highs PRIVATE ${basiclu_sources} ${ipx_sources} ipm/IpxWrapper.cpp)

if(UNIX)
  target_compile_options(highs PRIVATE "-Wno-unused-variable")
  target_compile_options(highs PRIVATE "-Wno-unused-const-variable")
endif()

find_package(Threads REQUIRED)
target_link_libraries(highs Threads::Threads)
