# Created by: Koichiro IWAO <meta+ports@vmeta.jp>
# $FreeBSD$

PORTNAME=	pluggaloid
PORTVERSION=	1.0.2
CATEGORIES=	devel rubygems
MASTER_SITES=	RG

MAINTAINER=	tota@FreeBSD.org
COMMENT=	Extensible plugin system for mikutter

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE.txt

RUN_DEPENDS=	rubygem-delayer>=0:${PORTSDIR}/devel/rubygem-delayer \
		rubygem-instance_storage>=1.0.0:${PORTSDIR}/devel/rubygem-instance_storage

NO_ARCH=	yes
USE_RUBY=	yes
USE_RUBYGEMS=	yes
RUBYGEM_AUTOPLIST=	yes

.include <bsd.port.mk>
