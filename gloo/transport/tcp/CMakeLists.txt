if(${CMAKE_SYSTEM_NAME} MATCHES "Darwin")
    message(WARNING "Gloo doesn't support OSX (uses epoll)")
else()
    list(APPEND GLOO_TRANSPORT_SRCS
      "${CMAKE_CURRENT_SOURCE_DIR}/address.cc"
      "${CMAKE_CURRENT_SOURCE_DIR}/buffer.cc"
      "${CMAKE_CURRENT_SOURCE_DIR}/context.cc"
      "${CMAKE_CURRENT_SOURCE_DIR}/device.cc"
      "${CMAKE_CURRENT_SOURCE_DIR}/loop.cc"
      "${CMAKE_CURRENT_SOURCE_DIR}/pair.cc"
      "${CMAKE_CURRENT_SOURCE_DIR}/unbound_buffer.cc"
      )
    list(APPEND GLOO_TRANSPORT_HDRS
      "${CMAKE_CURRENT_SOURCE_DIR}/address.h"
      "${CMAKE_CURRENT_SOURCE_DIR}/attr.h"
      "${CMAKE_CURRENT_SOURCE_DIR}/buffer.h"
      "${CMAKE_CURRENT_SOURCE_DIR}/context.h"
      "${CMAKE_CURRENT_SOURCE_DIR}/device.h"
      "${CMAKE_CURRENT_SOURCE_DIR}/loop.h"
      "${CMAKE_CURRENT_SOURCE_DIR}/pair.h"
      "${CMAKE_CURRENT_SOURCE_DIR}/unbound_buffer.h"
      )
endif()

if(GLOO_HAVE_TRANSPORT_TCP_TLS)
    add_subdirectory(tls)
endif()

set(GLOO_TRANSPORT_SRCS ${GLOO_TRANSPORT_SRCS} PARENT_SCOPE)
set(GLOO_TRANSPORT_HDRS ${GLOO_TRANSPORT_HDRS} PARENT_SCOPE)
