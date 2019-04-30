
add_lldb_library(lldbPluginProcessGDBRemote PLUGIN
  GDBRemoteClientBase.cpp
  GDBRemoteCommunication.cpp
  GDBRemoteCommunicationClient.cpp
  GDBRemoteCommunicationHistory.cpp
  GDBRemoteCommunicationReplayServer.cpp
  GDBRemoteCommunicationServer.cpp
  GDBRemoteCommunicationServerCommon.cpp
  GDBRemoteCommunicationServerLLGS.cpp
  GDBRemoteCommunicationServerPlatform.cpp
  GDBRemoteRegisterContext.cpp
  ProcessGDBRemote.cpp
  ProcessGDBRemoteLog.cpp
  ThreadGDBRemote.cpp

  LINK_LIBS
    lldbBreakpoint
    lldbCore
    lldbDataFormatters
    lldbHost
    lldbInterpreter
    lldbSymbol
    lldbTarget
    lldbUtility
  LINK_COMPONENTS
    Support
  )

target_include_directories(lldbPluginProcessGDBRemote PRIVATE
  ${LIBXML2_INCLUDE_DIR})
target_link_libraries(lldbPluginProcessGDBRemote PRIVATE
  lldbPluginProcessUtility
  lldbPluginPlatformMacOSX)
if(HAVE_LIBCOMPRESSION)
  target_link_libraries(lldbPluginProcessGDBRemote PRIVATE compression)
endif()
