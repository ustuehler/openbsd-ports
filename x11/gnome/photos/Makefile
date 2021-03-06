# $OpenBSD: Makefile,v 1.56 2017/07/13 10:35:29 jca Exp $

BROKEN-powerpc=		undefined reference to __sync_add_and_fetch_8

TRACKER_API=		1.0

COMMENT=		access, organize and share your photos on GNOME

GNOME_PROJECT=		gnome-photos
GNOME_VERSION=		3.24.2

CATEGORIES=		graphics

# GPLv2+
PERMIT_PACKAGE_CDROM=	Yes

WANTLIB += ICE SM X11 Xcomposite Xcursor Xdamage Xext Xfixes Xi
WANTLIB += Xinerama Xrandr Xrender atk-1.0 atk-bridge-2.0 atspi
WANTLIB += babl-0.1 c cairo cairo-gobject crypto curl dbus-1 epoxy
WANTLIB += exiv2 expat ffi fontconfig freetype gck-1 gcr-base-3
WANTLIB += gcrypt gdata gdk-3 gdk_pixbuf-2.0 gegl-0.3 geocode-glib
WANTLIB += gexiv2 gfbgraph-0.2 gio-2.0 glib-2.0 gmodule-2.0 gnome-desktop-3
WANTLIB += goa-1.0 gobject-2.0 gpg-error graphite2 grilo-0.3 gthread-2.0
WANTLIB += gtk-3 harfbuzz iconv icudata icui18n icuuc intl jpeg
WANTLIB += json-glib-1.0 kvm lzma m mediaart-2.0 nghttp2 nspr4
WANTLIB += nss3 oauth p11-kit pango-1.0 pangocairo-1.0 pangoft2-1.0
WANTLIB += pcre pixman-1 plc4 plds4 png pthread pthread-stubs
WANTLIB += rest-0.7 smime3 softokn3 soup-2.4 soup-gnome-2.4 sqlite3
WANTLIB += ssl ssl3 uuid xcb xcb-render xcb-shm xml2 z
WANTLIB += tracker-control-${TRACKER_API}
WANTLIB += tracker-sparql-${TRACKER_API}
WANTLIB += lib/tracker-${TRACKER_API}/tracker-data
WANTLIB += lib/tracker-${TRACKER_API}/tracker-common

MODULES=		devel/dconf \
			x11/gnome

MODGNOME_TOOLS=		desktop-file-utils gtk-update-icon-cache yelp

LIB_DEPENDS=		devel/libgdata \
			geo/geocode-glib \
			graphics/gegl03 \
			graphics/libgexiv2 \
			x11/gnome/desktop \
			x11/gnome/gfbgraph \
			x11/gnome/grilo \
			x11/gnome/online-accounts \
			x11/gnome/tracker

# com.intel.dleyna-renderer
RUN_DEPENDS +=		net/dleyna/renderer

# src/photos-application.c
RUN_DEPENDS +=		x11/gnome/online-miners

# calls grl_registry_load...plugin
RUN_DEPENDS +=		x11/gnome/grilo-plugins

.if ${MACHINE_ARCH} == i386
# undefined reference to `__sync_add_and_fetch_8'
CFLAGS +=		-march=i686
.endif

CONFIGURE_STYLE=	gnu

# XXX
# cc1: error: unrecognized command line option "-Wunused-but-set-variable"
# cc1: error: unrecognized command line option "-Warray-bounds"
pre-configure:
	sed -i -e 's,-Wunused-but-set-variable,,g' \
		-e 's,-Warray-bounds,,g' ${WRKSRC}/configure

.include <bsd.port.mk>
