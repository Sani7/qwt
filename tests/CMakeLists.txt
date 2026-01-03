file(GLOB SUBDIRS RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} "${CMAKE_CURRENT_SOURCE_DIR}/*")

foreach(SUBDIR ${SUBDIRS})
    if(IS_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/${SUBDIR})
        file(GLOB SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/${SUBDIR}/*.cpp" "${CMAKE_CURRENT_SOURCE_DIR}/${SUBDIR}/*.h")

        if(SOURCES)
            add_executable(${SUBDIR} ${SOURCES})

            target_include_directories(${SUBDIR} PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/${SUBDIR})

            target_link_libraries(${SUBDIR} qwt)
            if(NOT QWT_BUILD_TESTS)
                set_target_properties(${SUBDIR} PROPERTIES
                    EXCLUDE_FROM_ALL TRUE
                    EXCLUDE_FROM_DEFAULT_BUILD TRUE  # mainly for Visual Studio
                )
            endif()
        endif()
    endif()
endforeach()
