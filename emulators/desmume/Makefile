# $OpenBSD: Makefile,v 1.19 2017/07/26 22:45:19 sthen Exp $

USE_WXNEEDED =	Yes

COMMENT =	Nintendo DS emulator

DISTNAME =	desmume-0.9.11
REVISION =	4

CATEGORIES =	emulators

HOMEPAGE =	http://desmume.org/

MAINTAINER =	Anthony J. Bentley <anthony@anjbe.name>

# GPLv2+
PERMIT_PACKAGE_CDROM =		Yes

WANTLIB += agg c m pthread ${LIBCXX} z GL GLU X11 Xcomposite
WANTLIB += Xcursor Xdamage Xext Xfixes Xi Xinerama Xrandr Xrender
WANTLIB += fontconfig freetype gdk_pixbuf-2.0 gio-2.0
WANTLIB += glib-2.0 gobject-2.0 gthread-2.0 SDL SoundTouch
WANTLIB += atk-1.0 cairo gdk-x11-2.0 gtk-x11-2.0
WANTLIB += pango-1.0 pangocairo-1.0 pangoft2-1.0 zzip

MASTER_SITES =	${MASTER_SITE_SOURCEFORGE:=desmume/}

RUN_DEPENDS =	devel/desktop-file-utils

LIB_DEPENDS =	archivers/zziplib \
		audio/soundtouch \
		devel/sdl \
		graphics/agg \
		graphics/gdk-pixbuf2 \
		x11/gtk+2

CONFIGURE_ENV +=	CPPFLAGS="-I${LOCALBASE}/include -I${X11BASE}/include" \
			LDFLAGS="-L${LOCALBASE}/lib -L${X11BASE}/lib"

MODULES =	devel/gettext \
		textproc/intltool


COMPILER =	gcc

CONFIGURE_STYLE =	gnu

.include <bsd.port.mk>
