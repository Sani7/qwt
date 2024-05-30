if(EMSCRIPTEN)
    # WebAssembly specific code
else()
    find_package(QT NAMES Qt6 REQUIRED COMPONENTS Core Widgets UiPlugin Gui Designer)
    find_package(Qt6 REQUIRED COMPONENTS Core Widgets UiPlugin Gui Designer)

    qt_add_plugin(qwt_designer)

    target_include_directories(qwt_designer
      PRIVATE
      ../src/
      ${CMAKE_CURRENT_LIST_DIR}/
    #  ${PROJECT_BINARY_DIR}/
    )

    target_compile_definitions(qwt_designer
        PRIVATE
        "QWT_MOC_INCLUDE"
    )
    add_definitions(-DQT_PLUGIN)
    add_definitions(-DQT_NO_DEBUG)
    add_definitions(-DQT_SHARED)
    add_definitions(-DQDESIGNER_EXPORT_WIDGETS)

    target_sources(qwt_designer
      PRIVATE
      qwt_designer_plugin.cpp
      qwt_designer_plugin.qrc
    )

    target_link_libraries(qwt_designer
        PRIVATE
            Qt6::Core
            Qt6::Gui
            Qt6::UiPlugin
            Qt6::Widgets
            Qt6::Designer
            qwt
    )

endif()
