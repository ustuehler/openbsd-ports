# $OpenBSD: Makefile,v 1.54 2017/07/26 22:45:29 sthen Exp $

COMMENT =		labels and business card designer

GNOME_PROJECT =		glabels
GNOME_VERSION =		3.4.0
REVISION =		4

CATEGORIES =		productivity graphics

SHARED_LIBS +=  glabels-3.0               0.0 # 8.0
SHARED_LIBS +=  glbarcode-3.0             0.0 # 0.0

HOMEPAGE =		http://glabels.sourceforge.net

# GPLv3/LGPLv3/MIT      
# Attribution-ShareAlike 3.0 Unported
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB += EGL GL ICE SM X11 X11-xcb Xcomposite Xcursor Xdamage
WANTLIB += Xext Xfixes Xi Xinerama Xrandr Xrender Xt Xxf86vm atk-1.0
WANTLIB += atk-bridge-2.0 atspi c cairo cairo-gobject camel-1.2
WANTLIB += croco-0.6 db dbus-1 drm ebackend-1.2 ebook-1.2 ebook-contacts-1.2
WANTLIB += edata-book-1.2 edataserver-1.2 enchant epoxy $(LIBECXX)
WANTLIB += expat ffi fontconfig freetype gbm gck-1 gcr-base-3
WANTLIB += gcrypt gdk-3 gdk_pixbuf-2.0 gio-2.0 glapi glib-2.0
WANTLIB += gmodule-2.0 gobject-2.0 gpg-error graphite2 gstapp-1.0
WANTLIB += gstaudio-1.0 gstbase-1.0 gstfft-1.0 gstpbutils-1.0
WANTLIB += gstreamer-1.0 gsttag-1.0 gstvideo-1.0 gthread-2.0 gtk-3
WANTLIB += harfbuzz harfbuzz-icu hyphen iconv icudata icui18n
WANTLIB += icuuc iec16022 intl javascriptcoregtk-4.0 jpeg json-glib-1.0
WANTLIB += lzma m notify nspr4 nss3 nssutil3 orc-0.4 p11-kit pango-1.0
WANTLIB += pangocairo-1.0 pangoft2-1.0 pcre pixman-1 plc4 plds4
WANTLIB += png pthread pthread-stubs qrencode rsvg-2 secret-1
WANTLIB += smime3 softokn3 soup-2.4 sqlite3 ssl3 webkit2gtk-4.0
WANTLIB += webp xcb xcb-dri2 xcb-glx xcb-render xcb-shm xcb-xfixes
WANTLIB += xml2 xslt z zint

MODULES =		devel/dconf \
			x11/gnome

LIB_DEPENDS =		databases/evolution-data-server \
			graphics/iec16022 \
			graphics/libqrencode \
			graphics/zint \
			x11/gnome/librsvg \
			x11/gtk+3

MODGNOME_TOOLS =	desktop-file-utils gtk-update-icon-cache shared-mime-info yelp

CONFIGURE_STYLE =	gnu

.include <bsd.port.mk>
