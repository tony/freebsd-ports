# $FreeBSD$

PORTNAME=	compass-rails
PORTVERSION=	3.0.0
CATEGORIES=	textproc rubygems
MASTER_SITES=	RG

MAINTAINER=	ruby@FreeBSD.org
COMMENT=	Integrate Compass into Rails 2.3 and up

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

RUN_DEPENDS=	rubygem-compass>=1.0.0:${PORTSDIR}/textproc/rubygem-compass \
		rubygem-sass-rails5>=0:${PORTSDIR}/textproc/rubygem-sass-rails5 \
		rubygem-sprockets3>=0:${PORTSDIR}/devel/rubygem-sprockets3

NO_ARCH=	yes
USE_RUBY=	yes
USE_RUBYGEMS=	yes
RUBYGEM_AUTOPLIST=	yes

.include <bsd.port.mk>
