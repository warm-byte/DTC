IF("${GPROF}" EQUAL 1)
    ADD_COMPILE_OPTIONS(-pg)
ENDIF()
IF("${USE_REGPARM}" EQUAL 1)
    ADD_COMPILE_OPTIONS(-DCONFIG_REGPARM=3)
ENDIF()
IF("${HAVE_STATS}" EQUAL 1)
    ADD_COMPILE_OPTIONS(-DHAVE_STATS=1)
ENDIF()
IF("${USE_COMPATIBLE_MODE}" EQUAL 1)
    ADD_COMPILE_OPTIONS(-DUSE_COMPATIBLE_MODE=1)
ENDIF()
IF("${HAVE_ASSERT_LOG}" EQUAL 1)
    ADD_COMPILE_OPTIONS(-DHAVE_ASSERT_LOG=1)
ENDIF()

FILE(GLOB_RECURSE  SRC_LIST ./*.c)

INCLUDE_DIRECTORIES(
    .
    ./common 
    ./event 
    ./hashkit 
    ./proto
    ../libs/mxml/libs/include)

LINK_DIRECTORIES(
    ${PROJECT_SOURCE_DIR}/src/libs/mxml/libs
)

LINK_LIBRARIES(rt) 
LINK_LIBRARIES(libmxml.a)
LINK_LIBRARIES(pthread)

ADD_DEFINITIONS ("-D_GNU_SOURCE")

ADD_EXECUTABLE(dtcagent ${SRC_LIST})

TARGET_LINK_LIBRARIES(dtcagent libmxml.a)
