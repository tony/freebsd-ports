# $FreeBSD$
# pkg-help formatted with fmt 59 63

PORTNAME=	bind
PORTVERSION=	${ISCVERSION:S/-P/P/}
PORTREVISION=	0
CATEGORIES=	dns net ipv6
MASTER_SITES=	ISC/bind9/${ISCVERSION}
PKGNAMESUFFIX=	99
DISTNAME=	${PORTNAME}-${ISCVERSION}

MAINTAINER=	mat@FreeBSD.org
COMMENT=	BIND DNS suite with updated DNSSEC and DNS64

LICENSE=	ISCL

# ISC releases things like 9.8.0-P1, which our versioning doesn't like
ISCVERSION=	9.9.8-P3

MAKE_JOBS_UNSAFE=	yes

USES=	cpe libedit

CPE_VENDOR=	isc
CPE_VERSION=	${ISCVERSION:C/-.*//}
.if ${ISCVERSION:M*-*}
CPE_UPDATE=	${ISCVERSION:C/.*-//:tl}
.endif

LIB_DEPENDS=	libxml2.so:${PORTSDIR}/textproc/libxml2

GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--localstatedir=/var --disable-linux-caps \
		--disable-symtable \
		--with-randomdev=/dev/random \
		--with-libxml2=${LOCALBASE} \
		--with-readline=-ledit \
		--sysconfdir=${ETCDIR}
ETCDIR=		${PREFIX}/etc/namedb

CONFLICTS=	bind9*-9.[45678].* bind9*-sdb-9.[45678].* bind-tools-9.*

SUB_FILES=	pkg-message

OPTIONS_DEFAULT=	IPV6 SSL THREADS SIGCHASE IDN GSSAPI_NONE RRL
OPTIONS_DEFINE=		SSL IDN REPLACE_BASE LARGE_FILE FIXED_RRSET SIGCHASE \
			IPV6 THREADS FILTER_AAAA GOST PYTHON START_LATE MINCACHE \
			LINKS RPZ_NSIP RPZ_NSDNAME RRL DOCS RPZ_PATCH NEWSTATS \
			PORTREVISION FETCHLIMIT QUERYTRACE
OPTIONS_GROUP=		DLZ
OPTIONS_GROUP_DLZ=	DLZ_POSTGRESQL DLZ_MYSQL DLZ_BDB \
			DLZ_LDAP DLZ_FILESYSTEM DLZ_STUB
OPTIONS_SINGLE=		GSSAPI
OPTIONS_SINGLE_GSSAPI=	GSSAPI_BASE GSSAPI_HEIMDAL GSSAPI_MIT GSSAPI_NONE

OPTIONS_SUB=	yes

SSL_DESC=		Build with OpenSSL (Required for DNSSEC)
REPLACE_BASE_DESC=	EOL, no longer supported
LARGE_FILE_DESC=	64-bit file support
FIXED_RRSET_DESC=	Enable fixed rrset ordering
SIGCHASE_DESC=		dig/host/nslookup will do DNSSEC validation
FILTER_AAAA_DESC=	Enable filtering of AAAA records
GOST_DESC=		Enable GOST ciphers, needs SSL (see help on 8 and 9)
PYTHON_DESC=		Build with Python utilities
START_LATE_DESC=	Start BIND late in the boot process
MINCACHE_DESC=		Use the mincachettl patch
PORTREVISION_DESC=	Show PORTREVISION in the version string
FETCHLIMIT_DESC=	Enable the query quotas for resolvers
QUERYTRACE_DESC=	Enable the very verbose query tracelogging

LINKS_DESC=		Create conf file symlinks in ${PREFIX}
NEWSTATS_DESC=		Enable alternate xml statistics channel format
RPZ_NSIP_DESC=		Enable RPZ NSIP trigger rules
RPZ_NSDNAME_DESC=	Enable RPZ NSDNAME policy records
RPZ_PATCH_DESC=		RPZ improvements
RRL_DESC=		Response Rate Limiting
DLZ_DESC=		Dynamically Loadable Zones
DLZ_POSTGRESQL_DESC=	DLZ Postgres driver
DLZ_MYSQL_DESC=		DLZ MySQL driver (no threading)
DLZ_BDB_DESC=		DLZ BDB driver
DLZ_LDAP_DESC=		DLZ LDAP driver
DLZ_FILESYSTEM_DESC=	DLZ filesystem driver
DLZ_STUB_DESC=		DLZ stub driver
GSSAPI_BASE_DESC=	${GSSAPI_DESC} (Heimdal in base)
GSSAPI_HEIMDAL_DESC=	${GSSAPI_DESC} (security/heimdal)
GSSAPI_MIT_DESC=	${GSSAPI_DESC} (security/krb5)
GSSAPI_NONE_DESC=	No ${GSSAPI_DESC}
MINCACHE_EXTRA_PATCHES=	${FILESDIR}/extrapatch-bind-min-override-ttl
FETCHLIMIT_CONFIGURE_ENABLE=	fetchlimit
QUERYTRACE_CONFIGURE_ENABLE=	querytrace

SSL_CONFIGURE_ON=	--with-openssl=${OPENSSLBASE}
SSL_USE=		openssl=yes
SSL_CONFIGURE_OFF=	--disable-openssl-version-check --without-openssl

NEWSTATS_CONFIGURE_ENABLE=	newstats

IDN_USES=		iconv
IDN_CONFIGURE_ON=	--with-idn=${LOCALBASE} ${ICONV_CONFIGURE_BASE}
IDN_LIB_DEPENDS=	libidnkit.so:${PORTSDIR}/dns/idnkit
IDN_CONFIGURE_OFF=	--without-idn

LARGE_FILE_CONFIGURE_ENABLE=	largefile

SIGCHASE_CONFIGURE_ON=	STD_CDEFINES="-DDIG_SIGCHASE=1"

IPV6_CONFIGURE_ENABLE=	ipv6

FILTER_AAAA_CONFIGURE_ENABLE=	filter-aaaa

GOST_CONFIGURE_WITH=	gost

PYTHON_CONFIGURE_WITH=	python
PYTHON_USES=	python

DLZ_POSTGRESQL_CONFIGURE_ON=	--with-dlz-postgres=yes
DLZ_POSTGRESQL_USES=		pgsql

FIXED_RRSET_CONFIGURE_ENABLE=	fixed-rrset

RPZ_NSIP_CONFIGURE_ENABLE=	rpz-nsip

RPZ_NSDNAME_CONFIGURE_ENABLE=	rpz-nsdname

RPZ_PATCH_PATCHFILES=	${ISCVERSION}-rpz2+rl.14038.05.patch.xz:vix
RPZ_PATCH_PATCH_SITES=	http://ss.vix.su/~vjs/:vix LOCAL/mat/bind:vix

RRL_CONFIGURE_ENABLE=	rrl

DLZ_MYSQL_CONFIGURE_ON=	--with-dlz-mysql=yes
DLZ_MYSQL_USE=		mysql=yes

DLZ_BDB_CONFIGURE_ON=	--with-dlz-bdb=yes
DLZ_BDB_USE=		bdb=yes

DLZ_LDAP_CONFIGURE_ON=	--with-dlz-ldap=yes
DLZ_LDAP_USE=		openldap=yes

DLZ_FILESYSTEM_CONFIGURE_ON=	--with-dlz-filesystem=yes

DLZ_STUB_CONFIGURE_ON=	--with-dlz-stub=yes

START_LATE_SUB_LIST=	NAMED_REQUIRE="SERVERS cleanvar" \
			NAMED_BEFORE="LOGIN"
START_LATE_SUB_LIST_OFF=NAMED_REQUIRE="NETWORKING ldconfig syslogd" \
			NAMED_BEFORE="SERVERS"

GSSAPI_BASE_USES=	gssapi
GSSAPI_BASE_CONFIGURE_ON= \
	--with-gssapi=${GSSAPIBASEDIR} KRB5CONFIG="${KRB5CONFIG}"
GSSAPI_HEIMDAL_USES=	gssapi:heimdal
GSSAPI_HEIMDAL_CONFIGURE_ON= \
	--with-gssapi=${GSSAPIBASEDIR} KRB5CONFIG="${KRB5CONFIG}"
GSSAPI_MIT_USES=	gssapi:mit
GSSAPI_MIT_CONFIGURE_ON= \
	--with-gssapi=${GSSAPIBASEDIR} KRB5CONFIG="${KRB5CONFIG}"
GSSAPI_NONE_CONFIGURE_ON=	--without-gssapi

.include <bsd.port.options.mk>

.if !${PORT_OPTIONS:MLINKS}
PKGINSTALL=${NONEXISTENT}
.endif

.if ${PORT_OPTIONS:MTHREADS} && !${PORT_OPTIONS:MDLZ_MYSQL}
CONFIGURE_ARGS+=	--enable-threads
.else
CONFIGURE_ARGS+=	--disable-threads
.endif

.if ${PORT_OPTIONS:MREPLACE_BASE}
IGNORE=		REPLACE_BASE is no longer supported
.endif # REPLACE_BASE

.if ${OPSYS} == DragonFly || (${OPSYS} == FreeBSD && ${OSVERSION} >= 1000100)
PKGINSTALL=	${NONEXISTENT}
PLIST_SUB+=	NOBASE="" BASE="@comment "
SUB_LIST+=	NOBASE="" BASE="@comment "
USE_RC_SUBR+=	named
SUB_FILES+=	named.conf
.if ${PORT_OPTIONS:MGOST}
WITH_OPENSSL_PORT=yes
.endif
.else
PLIST_SUB+=	NOBASE="@comment " BASE=""
SUB_LIST+=	NOBASE="@comment " BASE=""
.if ${PORT_OPTIONS:MSSL}
WITH_OPENSSL_PORT=	yes
.endif
.endif

PKGDEINSTALL=	${PKGINSTALL}

PORTDOCS=	*

post-patch:
	@${REINPLACE_CMD} -e 's|readline/readline.h|editline/readline.h|; \
		s|readline/history.h|histedit.h|' \
		${WRKSRC}/bin/dig/nslookup.c ${WRKSRC}/bin/nsupdate/nsupdate.c
.for FILE in check/named-checkconf.8 named/named.8 nsupdate/nsupdate.1 \
	rndc/rndc.8
	@${REINPLACE_CMD} -e 's#/etc/named.conf#${ETCDIR}/named.conf#g' \
		-e 's#/etc/rndc.conf#${ETCDIR}/rndc.conf#g' \
		-e "s#/var\/run\/named\/named.pid#/var/run/named/pid#" \
		${WRKSRC}/bin/${FILE}
.endfor

.if ${PORTREVISION:N0}
post-patch-PORTREVISION-on:
	@${REINPLACE_CMD} -e '/EXTENSIONS/s#=$$#=_${PORTREVISION}#' \
		${WRKSRC}/version
.endif

post-configure:
	@${REINPLACE_CMD} -e '/^SO_LDFLAGS/s/-Wl,-rpath,/-rpath /' ${WRKSRC}/bin/tests/system/dlzexternal/Makefile

post-install:
.if ${PORT_OPTIONS:MDOCS}
	${MKDIR} ${STAGEDIR}${DOCSDIR}/arm
	${INSTALL_DATA} ${WRKSRC}/doc/arm/*.html ${STAGEDIR}${DOCSDIR}/arm
	${INSTALL_DATA} ${WRKSRC}/doc/arm/Bv9ARM.pdf ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/CHANGES ${WRKSRC}/COPYRIGHT ${WRKSRC}/FAQ \
		${WRKSRC}/HISTORY ${WRKSRC}/README ${STAGEDIR}${DOCSDIR}
.endif

.if ${OPSYS} == DragonFly || (${OPSYS} == FreeBSD && ${OSVERSION} >= 1000100)
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/mtree
	${MKDIR} ${STAGEDIR}${ETCDIR}
.for i in dynamic master slave working
	@${MKDIR} ${STAGEDIR}${ETCDIR}/$i
.endfor
	${INSTALL_DATA} ${WRKDIR}/named.conf ${STAGEDIR}${ETCDIR}/named.conf.sample
	${INSTALL_DATA} ${FILESDIR}/named.root ${STAGEDIR}${ETCDIR}
	${INSTALL_DATA} ${FILESDIR}/empty.db ${STAGEDIR}${ETCDIR}/master
	${INSTALL_DATA} ${FILESDIR}/localhost-forward.db ${STAGEDIR}${ETCDIR}/master
	${INSTALL_DATA} ${FILESDIR}/localhost-reverse.db ${STAGEDIR}${ETCDIR}/master
	${INSTALL_DATA} ${FILESDIR}/BIND.chroot.dist ${STAGEDIR}${PREFIX}/etc/mtree
	${INSTALL_DATA} ${FILESDIR}/BIND.chroot.local.dist ${STAGEDIR}${PREFIX}/etc/mtree
.endif
	${INSTALL_DATA} ${WRKSRC}/bin/rndc/rndc.conf \
		${STAGEDIR}${ETCDIR}/rndc.conf.sample

.include <bsd.port.mk>
