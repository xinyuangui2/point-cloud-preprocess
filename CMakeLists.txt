cmake_minimum_required(VERSION 3.1)

project(structure-point-cloud2 LANGUAGES CXX)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(EIGEN_DIR /media/xinyuangui/Data/eigen-git-mirror)

include_directories("${EIGEN_DIR}" bilateral_filtering/include bilateral_filtering /usr/include/x86_64-linux-gnu/ImageMagick-6 /usr/include/ImageMagick-6)

find_package(Qt5 COMPONENTS Core Quick REQUIRED Xml)

add_executable(${PROJECT_NAME} main.cpp qml.qrc BoundingBox.cpp Color.cpp GeometricObject.cpp  GeometryExporter.cpp GeometryProcessing.cpp GeospatialBoundingBox.cpp Image.cpp ImageProcessing.cpp bilateral_filtering/fft_3D/support_3D.cpp)
target_compile_definitions(${PROJECT_NAME} PRIVATE $<$<OR:$<CONFIG:Debug>,$<CONFIG:RelWithDebInfo>>:QT_QML_DEBUG>)
target_link_libraries(${PROJECT_NAME} PRIVATE Qt5::Core Qt5::Quick Qt5::Xml fftw3 Magick++-6.Q16 MagickWand-6.Q16 MagickCore-6.Q16 opencv_shape opencv_stitching opencv_superres opencv_videostab opencv_aruco opencv_bgsegm opencv_bioinspired opencv_ccalib opencv_datasets opencv_dpm opencv_face opencv_freetype opencv_fuzzy opencv_hdf opencv_line_descriptor opencv_optflow opencv_video opencv_plot opencv_reg opencv_saliency opencv_stereo opencv_structured_light opencv_phase_unwrapping opencv_rgbd opencv_viz opencv_surface_matching opencv_text opencv_ximgproc opencv_calib3d opencv_features2d opencv_flann opencv_xobjdetect opencv_objdetect opencv_ml opencv_xphoto opencv_highgui opencv_videoio opencv_imgcodecs opencv_photo opencv_imgproc opencv_core)
