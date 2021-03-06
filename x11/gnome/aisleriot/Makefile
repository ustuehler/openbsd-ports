# $OpenBSD: Makefile,v 1.23 2017/07/30 06:51:50 ajacoutot Exp $

COMMENT =		suite of solitaire card games

GNOME_PROJECT =		aisleriot
GNOME_VERSION =		3.22.2

CATEGORIES =		games

# GPLv2
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB += ICE SM X11 Xcomposite Xcursor Xdamage Xext Xfixes Xi
WANTLIB += Xinerama Xrandr Xrender atk-1.0 atk-bridge-2.0 atspi
WANTLIB += c cairo cairo-gobject canberra canberra-gtk3 croco-0.6
WANTLIB += dbus-1 dbus-glib-1 epoxy expat ffi fontconfig freetype
WANTLIB += gc gdk-3 gdk_pixbuf-2.0 gio-2.0 glib-2.0 gmodule-2.0
WANTLIB += gmp gobject-2.0 graphite2 gthread-2.0 gtk-3 guile-2.2
WANTLIB += harfbuzz iconv intl ltdl lzma m ogg pango-1.0 pangocairo-1.0
WANTLIB += pangoft2-1.0 pcre pixman-1 png pthread pthread-stubs
WANTLIB += rsvg-2 unistring vorbis vorbisfile xcb xcb-render xcb-shm
WANTLIB += xml2 z

MODULES =		devel/dconf \
			devel/gconf2 \
			x11/gnome

MODGNOME_TOOLS =	desktop-file-utils gtk-update-icon-cache yelp

# make it possible to build when both guile and guile2 are installed
# (takes precedence over -I${LOCALBASE}/include)
MODGNOME_CPPFLAGS =	-I${LOCALBASE}/include/guile/2.2

MODGCONF2_SCHEMAS_DIR =	aisleriot
CFLAGS += -Wno-strict-prototypes

# need to matche lang/guile2
COMPILER =		gcc
COMPILER_LANGS =	c

LIB_DEPENDS =		audio/libcanberra,-gtk3 \
			lang/guile2

BUILD_DEPENDS =		shells/bash

CONFIGURE_STYLE =	autoconf
AUTOCONF_VERSION =	2.69

CONFIGURE_ARGS =	--with-card-theme-formats=svg

CONFIGURE_ENV =		CONFIG_SHELL="${LOCALBASE}/bin/bash" \
			GUILE="${LOCALBASE}/bin/guile2" \
			GUILE_CONFIG="${LOCALBASE}/bin/guile2-config"

.include <bsd.port.mk>
