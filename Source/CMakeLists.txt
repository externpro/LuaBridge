set(LUABRIDGE_HEADERS
    LuaBridge/List.h
    LuaBridge/LuaBridge.h
    LuaBridge/Map.h
    LuaBridge/RefCountedObject.h
    LuaBridge/RefCountedPtr.h
    LuaBridge/UnorderedMap.h
    LuaBridge/Vector.h
    LuaBridge/Array.h
)

source_group("LuaBridge" FILES ${LUABRIDGE_HEADERS})

set(LUABRIDGE_DETAIL_HEADERS
    LuaBridge/detail/CFunctions.h
    LuaBridge/detail/ClassInfo.h
    LuaBridge/detail/Config.h
    LuaBridge/detail/Constructor.h
    LuaBridge/detail/dump.h
    LuaBridge/detail/FuncTraits.h
    LuaBridge/detail/Iterator.h
    LuaBridge/detail/LuaException.h
    LuaBridge/detail/LuaHelpers.h
    LuaBridge/detail/LuaRef.h
    LuaBridge/detail/Namespace.h
    LuaBridge/detail/Stack.h
    LuaBridge/detail/TypeList.h
    LuaBridge/detail/TypeTraits.h
    LuaBridge/detail/Userdata.h
)

source_group("LuaBridge\\detail" FILES ${LUABRIDGE_DETAIL_HEADERS})

add_library(LuaBridge INTERFACE)

target_include_directories(LuaBridge INTERFACE
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
)

if(LUABRIDGE_CXX17)
    target_compile_definitions(LuaBridge INTERFACE LUABRIDGE_CXX17)
endif()

if(MSVC AND CMAKE_SOURCE_DIR STREQUAL PROJECT_SOURCE_DIR)
    add_custom_target(LuaBridgeSources SOURCES
        ${LUABRIDGE_HEADERS}
        ${LUABRIDGE_DETAIL_HEADERS}
    )
endif()

if(DEFINED XP_NAMESPACE)
    set(targetsFile LuaBridgeTargets)
    set(XP_INSTALL_CMAKEDIR ${CMAKE_INSTALL_DATADIR}/cmake)
    xpPackageDevel(TARGETS_FILE ${targetsFile} DEPS lua LIBRARIES ${XP_NAMESPACE}::LuaBridge)
    install(TARGETS LuaBridge EXPORT ${targetsFile})
    install(EXPORT ${targetsFile} DESTINATION ${XP_INSTALL_CMAKEDIR} NAMESPACE ${XP_NAMESPACE}::)
endif()

if(CMAKE_SOURCE_DIR STREQUAL PROJECT_SOURCE_DIR)
    install(DIRECTORY LuaBridge TYPE INCLUDE)
endif()
