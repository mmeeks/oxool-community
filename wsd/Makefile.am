
oxool_includedir = $(includedir)/oxool/wsd

oxool_include_HEADERS = \
		Admin.hpp \
		AdminModel.hpp \
		Auth.hpp \
		ClientSession.hpp \
		DocumentBroker.hpp \
		Exceptions.hpp \
		FileServer.hpp \
		LOOLWSD.hpp \
		QueueHandler.hpp \
		SenderQueue.hpp \
		Storage.hpp \
		TileCache.hpp \
		TileDesc.hpp \
		TraceFile.hpp \
		UserMessages.hpp

include_paths = -I ${top_srcdir}/src/include -I${top_srcdir}/common -I${top_srcdir}/net -I${top_srcdir}/wsd -I${top_srcdir}/kit ${ZLIB_CFLAGS} ${FONTCONFIG_CFLAGS}

AM_CPPFLAGS = -pthread -DLOOLWSD_DATADIR='"@LOOLWSD_DATADIR@"' \
              -DLOOLWSD_CONFIGDIR='"@LOOLWSD_CONFIGDIR@"' \
              -DDEBUG_ABSSRCDIR='"@abs_top_srcdir@"' \
              ${include_paths}

if !ENABLE_DEBUG
AM_CPPFLAGS += -DNDEBUG
endif

AM_LDFLAGS = -pthread -Wl,-E,-rpath,/snap/oxoolwsd/current/usr/lib -lpam $(ZLIB_LIBS) ${FONTCONFIG_LIBS} $(top_builddir)/src/lib/liboxool.la

if ENABLE_SSL
AM_LDFLAGS += -lssl -lcrypto
else
oxool_LDADD = -lssl -lcrypto
endif

oxool_SOURCES = Admin.cpp \
		   AdminModel.cpp \
		   Auth.cpp \
		   DocumentBroker.cpp \
		   LOOLWSD.cpp \
		   ClientSession.cpp \
		   FileServer.cpp \
		   Storage.cpp \
		   TileCache.cpp

bin_PROGRAMS = oxool
		   
