# $FreeBSD$

PORTNAME=	acts-as-taggable-on
PORTVERSION=	2.4.1
CATEGORIES=	www rubygems
MASTER_SITES=	RG

MAINTAINER=	kuriyama@FreeBSD.org
COMMENT=	Tag a single model on several contexts

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE.md

RUN_DEPENDS=	rubygem-rails>=3.0:${PORTSDIR}/www/rubygem-rails

NO_ARCH=	yes
USE_RUBY=	YES
USE_RUBYGEMS=	YES
RUBYGEM_AUTOPLIST=	YES

BROKEN_RUBY23=	yes

.include <bsd.port.mk>
