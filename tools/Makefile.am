CXX = $(CXX_FOR_BUILD)
CPPFLAGS =
CXXFLAGS =
LDFLAGS =
LIBTOOL = @LIBTOOL@ --tag=CXX

EXTRA_CPPFLAGS = \
	$(dbus_CFLAGS) \
	$(expat_CFLAGS) \
	-I$(top_srcdir)/include \
	-I$(top_builddir)/include \
	-I$(top_builddir)/ctemplate \
	-DDATADIR=\"$(pkgdatadir)/\"
	-Wall

if CROSS_COMPILING
libdbus_cxx_la = $(BUILD_LIBDBUS_CXX_DIR)/libdbus-c++-1.la
else
libdbus_cxx_la = $(top_builddir)/src/libdbus-c++-1.la
endif

bin_PROGRAMS = dbusxx-xml2cpp dbusxx-introspect

dbusxx_xml2cpp_SOURCES = xml.h xml.cpp xml2cpp.h xml2cpp.cpp \
	generate_stubs.cpp generate_stubs.h  generator_utils.cpp  generator_utils.h
dbusxx_xml2cpp_CPPFLAGS = $(CPPFLAGS_FOR_BUILD) $(EXTRA_CPPFLAGS)
dbusxx_xml2cpp_CXXFLAGS = $(CXXFLAGS_FOR_BUILD)
dbusxx_xml2cpp_LDFLAGS = $(LDFLAGS_FOR_BUILD)
dbusxx_xml2cpp_LDADD = $(libdbus_cxx_la) $(expat_LIBS) -lctemplate_nothreads

dbusxx_introspect_SOURCES = introspect.h introspect.cpp
dbusxx_introspect_CPPFLAGS = $(CPPFLAGS_FOR_BUILD) $(EXTRA_CPPFLAGS)
dbusxx_introspect_CXXFLAGS = $(CXXFLAGS_FOR_BUILD)
dbusxx_introspect_LDFLAGS = $(LDFLAGS_FOR_BUILD)
dbusxx_introspect_LDADD = $(libdbus_cxx_la)

pkgdata_DATA = proxy-stubs.tpl adaptor-stubs.tpl ef-adaptor-stubs.tpl

MAINTAINERCLEANFILES = \
	Makefile.in
