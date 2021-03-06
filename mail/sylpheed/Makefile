# $OpenBSD: Makefile,v 1.115 2017/07/26 22:45:26 sthen Exp $

COMMENT =		lightweight and user-friendly e-mail client

DISTNAME =		sylpheed-3.5.1
REVISION =		1

SHARED_LIBS += 	 	sylph-0                   4.0 # 3.0
SHARED_LIBS += 		sylpheed-plugin-0         4.0 # 3.0

CATEGORIES =		mail news x11
HOMEPAGE =		http://sylpheed.sraoss.jp/en
MAINTAINER =		Amit Kulkarni <amitkulz@gmail.com>

# GPLv2 - LGPLv2
PERMIT_PACKAGE_CDROM =	Yes

MODULES =		devel/gettext

LIB_DEPENDS =		security/gpgme \
			textproc/gtkspell \
			x11/dbus-glib \
			x11/gtk+2

WANTLIB += X11 Xcomposite Xcursor Xdamage Xext Xfixes Xi Xinerama
WANTLIB += Xrandr Xrender assuan atk-1.0 c cairo crypto dbus-1
WANTLIB += dbus-glib-1 enchant expat ffi fontconfig freetype gdk-x11-2.0
WANTLIB += gdk_pixbuf-2.0 gio-2.0 glib-2.0 gmodule-2.0 gobject-2.0
WANTLIB += gpg-error gpgme graphite2 gthread-2.0 gtk-x11-2.0 gtkspell
WANTLIB += harfbuzz m pango-1.0 pangocairo-1.0 pangoft2-1.0 pcre
WANTLIB += pixman-1 png pthread pthread-stubs ssl ${COMPILER_LIBCXX} xcb
WANTLIB += xcb-render xcb-shm z

RUN_DEPENDS =		devel/desktop-file-utils
MASTER_SITES =		http://sylpheed.sraoss.jp/sylpheed/v3.5/

CONFIGURE_STYLE =	gnu
CONFIGURE_ARGS =	--disable-compface \
			--disable-jpilot \
			--enable-gpgme \
			--enable-gtkspell \
			--enable-ipv6 \
			--disable-ldap \
			--disable-oniguruma \
			--enable-ssl \
			--disable-updatecheck
CONFIGURE_ENV =		CPPFLAGS="-I${LOCALBASE}/include" \
			LDFLAGS="-L${LOCALBASE}/lib -pthread"

.include <bsd.port.mk>
