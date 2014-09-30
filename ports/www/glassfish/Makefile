# Created by: cjr@cruwe.de
# $FreeBSD$

PORTNAME=	glassfish
PORTVERSION=	4.1
CATEGORIES=	www java
MASTER_SITES=	http://dlc.sun.com.edgesuite.net/glassfish/${PORTVERSION}/release/

MAINTAINER=	cjr@cruwe.de
COMMENT=	Reference implementation of the Java EE application server

USES=		zip
USE_JAVA=	yes
JAVA_VERSION=	1.7+
NO_BUILD=	yes

WRKSRC=		${WRKDIR}/glassfish4
DATADIR=	${PREFIX}/${PORTNAME}-${PORTVERSION}

SUB_LIST=	GLASSFISHVERSION=${PORTVERSION}

DOWNLOAD_URL=	http://dlc.sun.com.edgesuite.net/glassfish/${PORTVERSION}/release/

USE_RC_SUBR=	glassfish
GLASSFISH_BIN_FILES=	appclient asadmin capture-schema jspc package-appclient schemagen startserv stopserv wscompile wsdeploy wsgen wsimport xjc

.include <bsd.port.pre.mk>

do-install:
	@${FIND} ${WRKSRC} -name '*.bat' -delete
	@${FIND} ${WRKSRC} -name '*.exe' -delete
	@(cd ${WRKSRC} && ${COPYTREE_SHARE} \* ${STAGEDIR}${DATADIR})
	@${CHMOD} ${BINMODE} ${STAGEDIR}${DATADIR}/bin/*
	@${CHMOD} ${BINMODE} ${STAGEDIR}${DATADIR}/mq/bin/*
.for x in ${GLASSFISH_BIN_FILES}
	@${CHMOD} ${BINMODE} ${STAGEDIR}${DATADIR}/glassfish/bin/${x}
.endfor

.include <bsd.port.post.mk>
