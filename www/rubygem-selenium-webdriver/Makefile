# Created by: Steve Wills <swills@FreeBSD.org>
# $FreeBSD$

PORTNAME=	selenium-webdriver
PORTVERSION=	3.14.1
PORTREVISION=	1
CATEGORIES=	www rubygems
MASTER_SITES=	RG

MAINTAINER=	ruby@FreeBSD.org
COMMENT=	Tool for writing automated tests of websites

LICENSE=	APACHE20
LICENSE_FILE=	${WRKSRC}/LICENSE

RUN_DEPENDS=	rubygem-childprocess>=0.5:devel/rubygem-childprocess \
		rubygem-rubyzip>=1.2.2:archivers/rubygem-rubyzip

USES=		gem
USE_RUBY=	yes
# do not strip files as this breaks the build of the port
# for more details: https://bugs.freebsd.org/bugzilla/show_bug.cgi?id=220330
STRIP_CMD=	${TRUE}

.include <bsd.port.mk>
