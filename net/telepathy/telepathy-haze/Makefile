# $OpenBSD: Makefile,v 1.28 2017/05/16 19:31:34 landry Exp $

COMMENT=		flexible communications framework, libpurple component

DISTNAME=		telepathy-haze-0.8.0
REVISION=		3

MASTER_SITES=		${MASTER_SITES_TP:=telepathy-haze/}

WANTLIB += c dbus-1 dbus-glib-1 gio-2.0 glib-2.0 gmodule-2.0 gobject-2.0
WANTLIB += gthread-2.0 m pcre pthread xml2 z purple telepathy-glib
WANTLIB += ffi idn gadu lzma

MODULES=		devel/gettext \
			lang/python

MODPY_RUNDEP=		No

BUILD_DEPENDS=		devel/py-twisted \
			net/py-xmpp \
			textproc/libxslt
LIB_DEPENDS=		net/pidgin,-libpurple \
			net/telepathy/telepathy-glib

.include <bsd.port.mk>
