
add_lldb_library(lldbInitialization
  SystemInitializerCommon.cpp
  SystemInitializer.cpp
  SystemLifetimeManager.cpp

  LINK_LIBS
    lldbCore
    lldbHost
    lldbPluginInstructionARM
    lldbPluginInstructionMIPS
    lldbPluginInstructionMIPS64
    lldbPluginProcessGDBRemote
    ${LLDB_SYSTEM_LIBS}
  LINK_COMPONENTS
    Support
  )
if(CMAKE_SYSTEM_NAME MATCHES "Linux|Android|FreeBSD|NetBSD")
  target_link_libraries(lldbInitialization PRIVATE lldbPluginProcessPOSIX)
endif()
if(CMAKE_SYSTEM_NAME MATCHES Windows)
  target_link_libraries(lldbInitialization PRIVATE
    lldbPluginProcessWindowsCommon)
endif()
