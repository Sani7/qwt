set(CMAKE_PREFIX_PATH "~/Qt/6.4.3/gcc_64/bin/" CACHE PATH "Path to Qt")

find_package(QT NAMES Qt6 REQUIRED COMPONENTS Core Concurrent OpenGLWidgets PrintSupport Svg Widgets)
find_package(Qt6 REQUIRED COMPONENTS Concurrent Core OpenGLWidgets PrintSupport Svg Widgets)

qt_add_library(qwt STATIC)

set_target_properties(
    qwt
    PROPERTIES
        AUTOMOC ON
        AUTORCC ON
)
target_compile_definitions(qwt
    PRIVATE
    "QWT_MOC_INCLUDE"
)


target_include_directories(qwt
  INTERFACE
  ${CMAKE_CURRENT_LIST_DIR}/
#  ${PROJECT_BINARY_DIR}/
)

file(GLOB_RECURSE QWT_SOURCES "*.cpp")
file(GLOB_RECURSE QWT_HEADERS "*.hpp" "*.h")
target_sources(qwt
  PRIVATE
  ${QWT_SOURCES}
  ${QWT_HEADERS}
)

target_link_libraries(qwt
    PUBLIC

    PRIVATE
        Qt6::Core
        Qt6::OpenGLWidgets
        Qt6::Widgets
        Qt6::Concurrent
        Qt6::PrintSupport
        Qt6::Svg
)
