# Created by: Daniel Gerzo <danger@FreeBSD.org>
# $FreeBSD$

PORTNAME=	maxminddb
PORTVERSION=	1.1.0
CATEGORIES=	devel net
PKGNAMEPREFIX=	php-

MAINTAINER=	danger@FreeBSD.org
COMMENT=	MaxMind DB Reader extension for PHP

LICENSE=	APACHE20

LIB_DEPENDS=	libmaxminddb.so:${PORTSDIR}/net/libmaxminddb

CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

USE_GITHUB=	yes
GH_ACCOUNT=	maxmind
GH_PROJECT=	MaxMind-DB-Reader-php
GH_TAGNAME=	1383655

WRKSRC_SUBDIR=	ext

USE_PHP=	yes
IGNORE_WITH_PHP=4
USE_PHPIZE=	yes
USE_PHPEXT=	yes
USES=		tar:tgz

.include <bsd.port.mk>
