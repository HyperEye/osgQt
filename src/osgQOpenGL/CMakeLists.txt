IF( Qt6Widgets_FOUND )
    include(GenerateExportHeader)

    SET(LIB_NAME osgQOpenGL)
    SET(HEADER_INSTALL_DIR osgQOpenGL)

    set(CMAKE_INCLUDE_CURRENT_DIR yes)

    SET(HEADER_PATH ../../include/osgQOpenGL)

    SET(SOURCE_H 
        ${HEADER_PATH}/osgQOpenGLWidget.h
        ${HEADER_PATH}/osgQOpenGLWindow.h
        ${HEADER_PATH}/OSGRenderer.h
    )

    qt6_wrap_cpp(SOURCES_H_MOC ${SOURCE_H} #[[OPTIONS ${MOC_OPTIONS}]])

    SET(TARGET_H
        ${SOURCE_H}
        ${HEADER_PATH}/CullVisitorEx.h
        ${HEADER_PATH}/GraphicsWindowEx.h
        ${HEADER_PATH}/RenderStageEx.h
        ${HEADER_PATH}/StateEx.h
        ${CMAKE_CURRENT_BINARY_DIR}/Export.h
    )


    SET(TARGET_SRC
        CullVisitorEx.cpp
        GraphicsWindowEx.cpp
        osgQOpenGLWidget.cpp
        osgQOpenGLWindow.cpp
        OSGRenderer.cpp
        RenderStageEx.cpp
        StateEx.cpp
        ${SOURCES_H_MOC}
        ${OPENSCENEGRAPH_VERSIONINFO_RC}
    )

    SET(TARGET_LIBRARIES Qt6::Widgets Qt6::OpenGL Qt6::OpenGLWidgets)
    SET(TARGET_LIBRARIES_VARS
        OSG_LIBRARY
        OSGUTIL_LIBRARY
        OSGVIEWER_LIBRARY
        OSGGA_LIBRARY
        OSGDB_LIBRARY
        OPENTHREADS_LIBRARY
    )

    SETUP_LIBRARY(${LIB_NAME})

    generate_export_header(${LIB_NAME} EXPORT_FILE_NAME "Export.h")

ENDIF()
