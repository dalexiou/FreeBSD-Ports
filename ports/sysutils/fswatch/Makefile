# Created by: Enrico M. Crisostomo <enrico.m.crisostomo@gmail.com>
# $FreeBSD$

PORTNAME=	fswatch
PORTVERSION=	1.4.5.1
CATEGORIES=	sysutils
MASTER_SITES=	https://github.com/emcrisostomo/fswatch/releases/download/${PORTVERSION}/
# The package name suffix is only used when testing the port with non-release
# source distributions (which currently use the -current suffix).
# PKGNAMESUFFIX=	-current

MAINTAINER=	enrico.m.crisostomo@gmail.com
COMMENT=	Cross-platform file change monitor

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/COPYING

# Overriding the fetch command because GitHub currently returns a 302 when
# downloading a file attached to a release.  The only way I know to follow
# the redirection is using wget.
FETCH_DEPENDS=	wget:${PORTSDIR}/ftp/wget

# Using:
#   * -nc: To avoid clobbering an existing file.
#   * --no-check-certificate: To ignore certificate validation, since GitHub
#                             certificate would not be accepted by wget.
FETCH_CMD=	wget
FETCH_BEFORE_ARGS=	-nc --no-check-certificate
DISABLE_SIZE=	yes

WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTVERSION}${PKGNAMESUFFIX}
USES=		zip libtool
USE_LDCONFIG=	yes
GNU_CONFIGURE=	yes

INFO=		fswatch

# fswatch may optionally use gettext
OPTIONS_DEFINE=	NLS
OPTIONS_SUB=	yes

NLS_USES=	gettext
NLS_CONFIGURE_ENABLE=	nls

post-install:
	  ${STRIP_CMD} ${STAGEDIR}${PREFIX}/lib/libfswatch.so

.include <bsd.port.mk>
