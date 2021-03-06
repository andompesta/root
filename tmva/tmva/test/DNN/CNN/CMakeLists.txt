############################################################################
# CMakeLists.txt file for building TMVA/DNN/CNN tests.
# @author Vladimir Ilievski
############################################################################

project(tmva-tests)
find_package(ROOT REQUIRED)

set(Libraries Core MathCore Matrix TMVA)
include_directories(${ROOT_INCLUDE_DIRS})

ROOT_EXECUTABLE(testIm2Col TestIm2Col.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-CNN-Im2Col COMMAND testIm2Col)

ROOT_EXECUTABLE(testDownsample TestDownsample.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-CNN-Downsample COMMAND testDownsample)

ROOT_EXECUTABLE(testFlatten TestFlatten.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-CNN-testFlatten COMMAND testFlatten)

ROOT_EXECUTABLE(testRotWeights TestRotateWeights.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-CNN-rotWeights COMMAND testrotWeights)

ROOT_EXECUTABLE(testForwardPass TestForwardPass.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-CNN-Forward COMMAND testForwardPass)

ROOT_EXECUTABLE(testConvNetLoss TestConvNetLoss.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-CNN-Loss COMMAND testConvNetLoss)

ROOT_EXECUTABLE(testConvNetPred TestConvNetPrediction.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-CNN-Pred COMMAND testConvNetPred)

ROOT_EXECUTABLE(testConvBackpropagation TestConvBackpropagation.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-CNN-Backpropagation COMMAND testConvBackpropagation)

ROOT_EXECUTABLE(testTensorDataLoader TestTensorDataLoader.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-Tensor-Data-Loader COMMAND testTensorDataLoader)

ROOT_EXECUTABLE(testDLMinimization TestMinimization.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-CNN-Minimization COMMAND testDLMinimization)

ROOT_EXECUTABLE(testMethodDL TestMethodDL.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-CNN-MethodDL COMMAND testMethodDL)

#--- CPU tests. ----------------------------
if (BLAS_FOUND AND imt)

include_directories(SYSTEM ${TBB_INCLUDE_DIRS})

ROOT_EXECUTABLE(testIm2ColCpu TestIm2ColCpu.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-CNN-Im2Col-CPU COMMAND testIm2ColCpu)

ROOT_EXECUTABLE(testDownsampleCpu TestDownsampleCpu.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-CNN-Downsample-CPU COMMAND testDownsampleCpu)

ROOT_EXECUTABLE(testRotWeightsCpu TestRotateWeightsCpu.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-CNN-rotWeights-CPU COMMAND testrotWeightsCpu)

ROOT_EXECUTABLE(testForwardPassCpu TestForwardPassCpu.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-CNN-Forward-CPU COMMAND testForwardPassCpu)

ROOT_EXECUTABLE(testConvNetLossCpu TestConvNetLossCpu.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-CNN-Loss-CPU COMMAND testConvNetLossCpu)

ROOT_EXECUTABLE(testConvNetPredCpu TestConvNetPredictionCpu.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-CNN-Pred-CPU COMMAND testConvNetPredCpu)

ROOT_EXECUTABLE(testTensorDataLoaderCpu TestTensorDataLoaderCpu.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-Tensor-Data-Loader-CPU COMMAND testTensorDataLoaderCpu)

ROOT_EXECUTABLE(testDLMinimizationCpu TestMinimizationCpu.cxx LIBRARIES ${Libraries})
ROOT_ADD_TEST(TMVA-DNN-CNN-Minimization-CPU COMMAND testDLMinimizationCpu)

endif (BLAS_FOUND AND imt)
