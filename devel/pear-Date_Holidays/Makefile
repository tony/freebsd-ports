# Created by: Thomas Abthorpe <thomas@goodking.ca>
# $FreeBSD$

PORTNAME=	Date_Holidays
PORTVERSION=	0.21.8
CATEGORIES=	devel www pear

MAINTAINER=	miwi@FreeBSD.org
COMMENT=	PEAR driver based class to calculate holidays

BUILD_DEPENDS=	${PEARDIR}/Date.php:${PORTSDIR}/devel/pear-Date \
		${PEARDIR}/XML/Serializer.php:${PORTSDIR}/devel/pear-XML_Serializer
RUN_DEPENDS=	${PEARDIR}/Date.php:${PORTSDIR}/devel/pear-Date \
		${PEARDIR}/XML/Serializer.php:${PORTSDIR}/devel/pear-XML_Serializer

USES=		pear

OPTIONS_DEFINE=	PEAR_CONSOLE_GETARGS
PEAR_CONSOLE_GETARGS_DESC=	Console::Getargs support

PEAR_CONSOLE_GETARGS_BUILD_DEPENDS=${PEARDIR}/Console/Getargs.php:${PORTSDIR}/devel/pear-Console_Getargs

.include <bsd.port.mk>
