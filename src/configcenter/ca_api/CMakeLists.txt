INCLUDE_DIRECTORIES(.)
    
AUX_SOURCE_DIRECTORY(. SRC_LIST1)

ADD_DEFINITIONS("-g -Wall -fPIC")

ADD_EXECUTABLE(client-tool ${SRC_LIST1})
ADD_LIBRARY(app-client ${SRC_LIST1})


