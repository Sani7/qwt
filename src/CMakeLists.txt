set(CMAKE_PREFIX_PATH "~/Qt/6.4.3/gcc_64/bin/" CACHE PATH "Path to Qt")

find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Core Concurrent OpenGLWidgets PrintSupport Svg Widgets)
find_package(Qt6 REQUIRED COMPONENTS Concurrent Core OpenGLWidgets PrintSupport Svg Widgets)

qt_add_library(qwt STATIC)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

target_include_directories(qwt
  PUBLIC
  ${CMAKE_CURRENT_LIST_DIR}/
  ${PROJECT_BINARY_DIR}
)

file(GLOB_RECURSE TEST_SOURCES "*.cpp")
target_sources(qwt
  PRIVATE
  ${TEST_SOURCES}
)

target_link_libraries(qwt
       PUBLIC
               Qt6::Core
               Qt6::OpenGLWidgets
       PRIVATE
               Qt6::Concurrent
               Qt6::PrintSupport
               Qt6::Svg
)
