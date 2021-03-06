# $FreeBSD$

PORTNAME=	go-git
DISTVERSIONPREFIX=	v
DISTVERSION=	4.10.0
CATEGORIES=	devel

MAINTAINER=	miwi@FreeBSD.org
COMMENT=	Highly extensible git implementation in pure Go

LICENSE=	APACHE20
LICENSE_FILE=	${WRKSRC}/LICENSE

USES=		go
USE_GITHUB=	yes
GH_ACCOUNT=	src-d
GO_PKGNAME=	gopkg.in/src-d/go-git.v4
GH_SUBDIR=	src/github.com/${GH_ACCOUNT}/${PORTNAME}
GH_TUPLE=	golang:crypto:505ab14:crypto/vendor/golang.org/x/crypto \
		golang:net:04a2e54:net/vendor/golang.org/x/net \
		golang:text:f21a4df:golangtext/vendor/golang.org/x/text \
		pelletier:go-buffruneio:v0.2.0:gotoml/vendor/github.com/pelletier/go-buffruneio \
		pkg:errors:v0.8.0:errors/vendor/github.com/pkg/errors \
		sergi:go-diff:v1.0.0:godiff/vendor/github.com/sergi/go-diff \
		gliderlabs:ssh:v0.1.1:ssh/vendor/github.com/gliderlabs/ssh \
		google:go-cmp:v0.2.0:gocmp/vendor/github.com/google/go-cmp  \
		emirpasic:gods:v1.9.0:gods/vendor/github.com/emirpasic/gods \
		jbenet:go-context:d14ea06fba99:gocontext/vendor/github.com/jbenet/go-context \
		jessevdk:go-flags:v1.4.0:goflags/vendor/github.com/jessevdk/go-flags \
		mitchellh:go-homedir:v1.0.0:gohomedir/vendor/github.com/mitchellh/go-homedir \
		xanzy:ssh-agent:v0.2.0:sshagent/vendor/github.com/xanzy/ssh-agent \
		kevinburke:ssh_config:81db2a75821e:sshconfig/vendor/github.com/kevinburke/ssh_config \
		src-d:go-git-fixtures:v3.1.1:gogitfixtures/vendor/gopkg.in/src-d/go-git-fixtures.v3 \
		src-d:go-billy:v4.2.1:gobilly/vendor/gopkg.in/src-d/go-billy.v4 \
		src-d:gcfg:v1.4.0:gcfg/vendor/github.com/src-d/gcfg \
		go-warnings:warnings:v0.1.2:warnings/vendor/gopkg.in/warnings.v0

PLIST_FILES=	bin/go-git
MAKE_ENV+=	GOFLAGS=-mod=vendor

do-build:
	(cd ${GO_WRKSRC}/cli/go-git/; \
	    ${SETENV} ${MAKE_ENV} ${GO_ENV} ${GO_CMD} build )

do-install:
	${INSTALL_PROGRAM} ${GO_WRKSRC}/cli/go-git/go-git ${STAGEDIR}${PREFIX}/bin/

.include <bsd.port.mk>
