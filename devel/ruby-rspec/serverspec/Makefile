# $OpenBSD: Makefile,v 1.35 2017/05/27 14:04:38 jasper Exp $

PORTROACH=	limitw:1,even

COMMENT=	RSpec tests for testing machine configuration/state

DISTNAME=	serverspec-2.38.1

HOMEPAGE=	http://serverspec.org/

MAINTAINER=	Jasper Lievisse Adriaanse <jasper@openbsd.org>

BUILD_DEPENDS=	${RUN_DEPENDS}
RUN_DEPENDS=	converters/ruby-multi_json,${MODRUBY_FLAVOR} \
		devel/ruby-rspec/3/rspec,${MODRUBY_FLAVOR} \
		devel/ruby-rspec/3/its,${MODRUBY_FLAVOR} \
		devel/ruby-rspec/specinfra,${MODRUBY_FLAVOR}>=2.43.9

MODRUBY_TEST=	rspec3
TEST_DEPENDS=	devel/ruby-rspec/3/its,${MODRUBY_FLAVOR}

.include <bsd.port.mk>
