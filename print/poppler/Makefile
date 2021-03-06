# $OpenBSD: Makefile,v 1.124 2017/07/26 22:45:29 sthen Exp $

COMMENT-main=	PDF rendering library
COMMENT-qt4=	qt4 interface to PDF rendering library
COMMENT-qt5=	Qt5 interface to PDF rendering library
COMMENT-utils=	PDF conversion tools and utilities

V=		0.52.0
DISTNAME=	poppler-$V
CATEGORIES=	print
PKGNAME-main=	poppler-$V
PKGNAME-utils=	poppler-utils-$V
PKGNAME-qt4=	poppler-qt4-$V
PKGNAME-qt5=	poppler-qt5-$V
REVISION-qt5=	1
REVISION-main=	0
REVISION-qt4=	0
REVISION-utils=	0

EXTRACT_SUFX=	.tar.xz

SHARED_LIBS +=	poppler              43.1     # 66.0
SHARED_LIBS +=	poppler-glib         16.0     # 16.0
SHARED_LIBS +=	poppler-qt4          20.1     # 15.0
SHARED_LIBS +=	poppler-qt5          3.1      # 10.0
SHARED_LIBS +=	poppler-cpp          8.0      # 3.0

HOMEPAGE=	http://poppler.freedesktop.org/

MAINTAINER=	Matthias Kilian <kili@openbsd.org>

# GPLv2
PERMIT_PACKAGE_CDROM=	Yes

MASTER_SITES=	${HOMEPAGE}

PSEUDO_FLAVORS=no_qt4 no_qt5 bootstrap
# XXX not strictly a bootstrap loop, but on the critical path for libreoffice
FLAVOR?=no_qt4 no_qt5 bootstrap

NOT_FOR_ARCHS-qt4 = arm
NOT_FOR_ARCHS-qt5 = arm

MULTI_PACKAGES=-main -qt4 -qt5 -utils

.include <bsd.port.arch.mk>

cWANTLIB=	expat freetype fontconfig jpeg m pthread tiff z

.if ${BUILD_PACKAGES:M-qt4}
MODULES+=	x11/qt4
.else
CONFIGURE_ARGS+=	--disable-poppler-qt4
.endif

.if ${BUILD_PACKAGES:M-qt5}
MODULES+=	x11/qt5
.else
CONFIGURE_ARGS+=	--disable-poppler-qt5
.endif

BUILD_DEPENDS+= devel/gobject-introspection

RUN_DEPENDS-main= \
		print/poppler-data>=0.4.7

LIB_DEPENDS-main= \
		converters/libiconv \
		devel/gettext \
		devel/glib2 \
		graphics/cairo \
		graphics/lcms2 \
		graphics/openjp2 \
		graphics/png \
		graphics/tiff

LIB_DEPENDS-qt4=${MODQT4_LIB_DEPENDS} \
		print/poppler

LIB_DEPENDS-qt5=${MODQT5_LIB_DEPENDS} \
		print/poppler

LIB_DEPENDS-utils= print/poppler

WANTLIB-main=	${cWANTLIB} Xext ffi gio-2.0 glib-2.0 gmodule-2.0 \
		gobject-2.0 pixman-1 openjp2 X11 Xrender cairo pcre \
		png pthread-stubs xcb xcb-render lcms2 xcb-shm \
		iconv intl ${LIBCXX}

WANTLIB-qt4=    ${cWANTLIB} ${MODQT4_WANTLIB} ICE QtCore QtGui QtXml \
		SM X11 Xext Xi Xinerama Xrender ffi glib-2.0 \
		gobject-2.0 gthread-2.0 iconv intl lcms2 openjp2 \
		png poppler pcre pthread-stubs ${LIBCXX} xcb

WANTLIB-qt5=	${cWANTLIB} $(LIBECXX) \
		GL Qt5Core Qt5Gui Qt5Widgets Qt5Xml X11 X11-xcb \
		Xdamage Xext Xfixes Xxf86vm drm execinfo ffi glapi \
		glib-2.0 gobject-2.0 graphite2 gthread-2.0 harfbuzz \
		iconv icudata icui18n icuuc intl lcms2 openjp2 pcre \
		pcre16 png poppler pthread-stubs xcb xcb-dri2 xcb-glx

WANTLIB-utils=	X11 Xext Xrender c cairo fontconfig lcms2 m pixman-1 \
		png pthread-stubs ${LIBCXX} xcb xcb-render xcb-shm openjp2 \
		poppler z ${cWANTLIB}

CONFIGURE_STYLE=autoconf
AUTOCONF_VERSION=2.69
CONFIGURE_ARGS+=--enable-xpdf-headers \
		--enable-poppler-cpp \
		--enable-utils \
		--enable-zlib \
		--disable-gtk-test \
		--disable-libnss \
		POPPLER_QT5_CXXFLAGS="-std=c++11"

CONFIGURE_ENV+= CPPFLAGS="-I${X11BASE}/include -I${LOCALBASE}/include" \
		LDFLAGS="-L${LOCALBASE}/lib" \
		LIBJPEG_CFLAGS="-I${LOCALBASE}/include" \
		ac_cv_prog_MOCQT4=${MODQT4_MOC}

USE_GMAKE=	Yes

MAIN_CC=	/usr/bin/cc
MAIN_CXX=	/usr/bin/c++
.if "${USE_CCACHE:L}" == "yes"
MAIN_CC:=	ccache ${MAIN_CC}
MAIN_CXX:=	ccache ${MAIN_CXX}
.endif

post-configure:
	find ${WRKBUILD} -name Makefile \! -path '*/qt5/*' -print0 | xargs -0 \
		perl -pi -e     's,^CC = \S+,override CC = ${MAIN_CC},;' \
		         -e    's,^CPP = \S+,override CPP = ${MAIN_CC},;' \
		         -e    's,^CXX = \S+,override CXX = ${MAIN_CXX},;' \
		         -e 's,^CXXCPP = \S+,override CXXCPP = ${MAIN_CXX},;'
	find ${WRKBUILD}/qt5 -name Makefile -print0 | xargs -0 \
		perl -pi -e     's,^CXXFLAGS =.*,$$& \$$(POPPLER_QT5_CXXFLAGS),;'

.include <bsd.port.mk>
