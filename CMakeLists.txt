cmake_minimum_required(VERSION 3.10)

project(04MVID CXX C)

set(CMAKE_CONFIGURATION_TYPES "Debug;Release" CACHE STRING "Config types" FORCE)
set_property(GLOBAL PROPERTY USE_FOLDERS ON)

#Files for dependencies and platform specific config
include(cmake/deps_files.cmake)
include(cmake/platform.cmake)
include(cmake/compiler.cmake)

#****************************************************
# Engine Library
#****************************************************
#Engine Source Files

set(ENGINE_SRC_FILES
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/object.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/engine.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/gameObject.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/managers/messageManager.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/managers/materialManager.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/transformComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/inputComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/cameraComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/cameraInputComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/renderComponent/cubeComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/renderComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/renderComponent/quadComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/renderComponent/sphereComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/renderComponent/teapotComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/renderComponent/uiTextComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/renderComponent/meshComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/renderComponent/modelComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/physicComponent/colliderComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/physicComponent/boxColliderComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/physicComponent/circleColliderComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/physicComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/lightComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/lightComponent/directionalLightComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/lightComponent/pointLightComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/components/lightComponent/spotLightComponent.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/systems/cameraSystem.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/systems/transformSystem.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/systems/inputSystem.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/systems/physicSystem.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/systems/shadowFBO.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/systems/lightSystem.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/systems/renderSystem.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/gpu.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/deps.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/shader.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/texture.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/material.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/fbo/fbo.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/window.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/ui/uiTextObject.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/ui/scoreUIObject.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/ui/lifesUIObject.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/ui/finalUIObject.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/gameManager.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/camera.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/quad.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/cube.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/sphere.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/teapot.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/directionalLight.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/pointLight.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/spotLight.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/wall.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/bar.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/ball.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/bricks/brick.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/engine/defaultObjects/bricks/simpleBrick.cpp)

set(ENGINE_HEADER_FILES
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/object.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/engine.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/gameObject.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/managers/gameObjectManager.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/managers/messageManager.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/managers/componentManager.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/managers/materialManager.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/component.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/cameraComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/transformComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/inputComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/cameraInputComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/renderComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/renderComponent/cubeComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/renderComponent/quadComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/renderComponent/sphereComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/renderComponent/teapotComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/renderComponent/teapotdata.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/renderComponent/uiTextComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/renderComponent/meshComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/renderComponent/modelComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/physicComponent/colliderComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/physicComponent/boxColliderComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/physicComponent/circleColliderComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/physicComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/lightComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/lightComponent/directionalLightComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/lightComponent/pointLightComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/components/lightComponent/spotLightComponent.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/systems/system.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/systems/cameraSystem.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/systems/transformSystem.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/systems/inputSystem.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/systems/physicSystem.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/systems/shadowFBO.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/systems/lightSystem.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/systems/renderSystem.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/gpu.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/shader.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/texture.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/material.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/fbo/fbo.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/window.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/ui/uiTextObject.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/ui/scoreUIObject.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/ui/lifesUIObject.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/ui/finalUIObject.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/gameManager.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/camera.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/quad.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/cube.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/sphere.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/teapot.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/pointLight.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/spotLight.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/directionalLight.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/wall.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/wall.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/bar.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/ball.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/bricks/brick.hpp
    ${CMAKE_CURRENT_LIST_DIR}/include/engine/defaultObjects/bricks/simpleBrick.hpp)

source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR}/src/engine/ PREFIX "Source Files" FILES ${ENGINE_SRC_FILES})
source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR}/include/engine PREFIX "Header Files" FILES ${ENGINE_HEADER_FILES})

add_library(EngineLib STATIC ${ENGINE_SRC_FILES} ${ENGINE_HEADER_FILES} ${DEPS_SRC_FILES_COMMON})

target_include_directories(EngineLib PRIVATE ${INCLUDE_PATHS})
target_link_libraries(EngineLib PRIVATE
    debug ${CMAKE_CURRENT_LIST_DIR}/libs/Debug/assimp-vc142-mt.lib
    optimized ${CMAKE_CURRENT_LIST_DIR}/libs/Release/assimp-vc142-mt.lib)
target_compile_definitions(EngineLib PRIVATE -D_GLFW_USE_OPENGL=1)
target_compile_features(EngineLib PRIVATE cxx_std_14)

configure_platform(EngineLib)
configure_compiler(EngineLib)

add_custom_command(TARGET EngineLib POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
    "${CMAKE_CURRENT_LIST_DIR}/libs/$<CONFIGURATION>/assimp-vc142-mt.dll"
    $<TARGET_FILE_DIR:EngineLib>)

#****************************************************
# Projects
#****************************************************
# List of projects
set(PROJECT_LIST FINAL)

#Root path of the projects
set(PROJECTS_PATH ${CMAKE_CURRENT_LIST_DIR}/projects)
#Configure All Projects
foreach(PROJECT ${PROJECT_LIST})
    message("Generating Project " ${PROJECT})

    #Create Directory and main.cpp
    file(MAKE_DIRECTORY ${PROJECTS_PATH}/${PROJECT})
    file(TOUCH ${PROJECTS_PATH}/${PROJECT}/main.cpp)

    #Create Project and configure
    add_executable(${PROJECT} ${PROJECTS_PATH}/${PROJECT}/main.cpp ${DEPS_SRC_FILES})
    target_include_directories(${PROJECT} PRIVATE ${INCLUDE_PATHS})
    target_compile_definitions(${PROJECT} PRIVATE -D_GLFW_USE_OPENGL=1)
    target_link_libraries(${PROJECT} PRIVATE EngineLib)
    target_compile_features(${PROJECT} PRIVATE cxx_std_14)
    configure_platform(${PROJECT})
    configure_compiler(${PROJECT})
endforeach()