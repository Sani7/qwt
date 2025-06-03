find_package(QT NAMES Qt6 REQUIRED COMPONENTS Core Concurrent OpenGLWidgets PrintSupport Svg Widgets)
find_package(Qt6 REQUIRED COMPONENTS Concurrent Core OpenGLWidgets PrintSupport Svg Widgets)

qt_add_library(qwt STATIC)

set_target_properties(
    qwt
    PROPERTIES
        AUTOMOC ON
        AUTORCC ON
)
set_property(TARGET qwt PROPERTY POSITION_INDEPENDENT_CODE ON)
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

if (EMSCRIPTEN)
  set(EXCLUDED_FILES
      "${CMAKE_CURRENT_SOURCE_DIR}/qwt_date_scale_draw.cpp"
      "${CMAKE_CURRENT_SOURCE_DIR}/qwt_date_scale_draw.h"
      "${CMAKE_CURRENT_SOURCE_DIR}/qwt_date_scale_engine.cpp"
      "${CMAKE_CURRENT_SOURCE_DIR}/qwt_date_scale_engine.h"
      "${CMAKE_CURRENT_SOURCE_DIR}/qwt_date.cpp"
      "${CMAKE_CURRENT_SOURCE_DIR}/qwt_date.h"
  )

  # Remove them from the list
  foreach(file_to_exclude IN LISTS EXCLUDED_FILES)
    list(REMOVE_ITEM QWT_SOURCES "${file_to_exclude}")
    list(REMOVE_ITEM QWT_HEADERS "${file_to_exclude}")
  endforeach()
endif()

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
