# Created by: Gasol Wu <gasol.wu@gmail.com>
# $FreeBSD$

PORTNAME=	fXSL
PORTVERSION=	1.1.0
CATEGORIES=	devel pear
MASTER_SITES=	http://pear.netpirates.net/get/
PKGNAMEPREFIX=	pear-TheSeer_
EXTRACT_SUFX=	.tgz

MAINTAINER=	gasol.wu@gmail.com
COMMENT=	XSL wrapper / extension to the PHP 5.x XSLTProcessor

LICENSE=	BSD3CLAUSE

BUILD_DEPENDS=	${PEARDIR}/.channels/pear.netpirates.net.reg:${PORTSDIR}/devel/pear-channel-theseer
RUN_DEPENDS=	${PEARDIR}/.channels/pear.netpirates.net.reg:${PORTSDIR}/devel/pear-channel-theseer

USE_PHP=	dom xml xsl
PEAR_CHANNEL=	theseer
USES=	pear

.include <bsd.port.mk>
