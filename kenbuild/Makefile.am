bin_PROGRAMS = kenbuild kenbuild-build

include $(top_srcdir)/Makefile.amshared

AM_CPPFLAGS=$(optionflags) -I$(srcdir)/../include
AM_CFLAGS=-W -Wall -Wimplicit -Wno-char-subscripts -Wno-unused \
          -funsigned-char -fno-pic -fno-strict-aliasing
WINDRESFLAGS=--include-dir=. --include-dir=.. --include-dir=$(srcdir)/../include

kenbuild_SOURCES=game.c sound_stub.c config.c
kenbuild_LDADD=../src/libengine.la
nodist_EXTRA_kenbuild_SOURCES=dummy.cxx

kenbuild_build_SOURCES=bstub.c
kenbuild_build_LDADD=../src/libeditor.a ../src/libengine.la
nodist_EXTRA_kenbuild_build_SOURCES=dummy.cxx

if RENDERTYPEWIN
kenbuild_SOURCES += startwin.game.c rsrc/gameres.rc
kenbuild_LDADD += $(WINDOWS_LDADD)

kenbuild_build_SOURCES += rsrc/buildres.rc
kenbuild_build_LDADD += $(WINDOWS_LDADD)
endif

if RENDERTYPESDL
kenbuild_SOURCES += rsrc/game_icon.c
kenbuild_build_SOURCES += rsrc/build_icon.c

kenbuild_LDADD += -lm $(SDL_LIBS)
kenbuild_build_LDADD += -lm $(SDL_LIBS)

if HAVE_GTK2
AM_CPPFLAGS += $(GTK_CFLAGS)

kenbuild_SOURCES += startgtk.game.c rsrc/game_banner.c
kenbuild_build_SOURCES += rsrc/editor_banner.c
endif

endif
