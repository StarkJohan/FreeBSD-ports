# $FreeBSD$

PORTNAME=	vault
PORTVERSION=	1.1.2
PORTREVISION=	1
DISTVERSIONPREFIX=	v
CATEGORIES=	security

MAINTAINER=	swills@FreeBSD.org
COMMENT=	Tool for securely accessing secrets

LICENSE=	MPL20
LICENSE_FILE=	${WRKSRC}/LICENSE

USES=		go

USE_GITHUB=	yes
GH_TUPLE=	hashicorp:${PORTNAME}:${VAULTTAG}:DEFAULT/src/github.com/hashicorp/${PORTNAME} \
		swills:vaultui:${VAULTUITAG}:vaultui

VAULTTAG=	${DISTVERSIONPREFIX}${PORTVERSION}
VAULTUITAG=	${DISTVERSIONPREFIX}${PORTVERSION}

USE_RC_SUBR=	vault

USERS=		vault
GROUPS=		vault

PLIST_FILES=	bin/${PORTNAME}
SUB_FILES=	pkg-message

post-patch:
	@${CP} ${WRKDIR}/vaultui-${PORTVERSION}/http/bindata_assetfs.go ${WRKDIR}/vault-${PORTVERSION}/http/bindata_assetfs.go

do-build:
	@cd ${WRKSRC}; \
		${SETENV} ${MAKE_ENV} ${BUILD_ENV} CGO_ENABLED=0 GOPATH=${WRKSRC} \
		go build \
		-tags=ui \
		-ldflags "\
		-X github.com/hashicorp/vault/version.Version=${PORTVERSION} \
		-X github.com/hashicorp/vault/version.VersionPrerelease= \
		-X github.com/hashicorp/vault/version.VersionMetadata= \
		-X github.com/hashicorp/vault/version.GitCommit='${COMMIT_ID}'" \
		-o bin/${PORTNAME}

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/bin/${PORTNAME} ${STAGEDIR}${PREFIX}/bin/${PORTNAME}

.include <bsd.port.mk>
