FROM bitnami/oraclelinux-extras:7-r17
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages ImageMagick cyrus-sasl-lib ghostscript glibc imagemagick keyutils-libs krb5-libs libcom_err libcurl libgcc libidn libselinux libssh2 libstdc++ libxml2 libxslt ncurses-libs nspr nss nss-softokn-freebl nss-util openldap openssl-libs pcre postgresql-libs readline sendmail xz-libs zlib
RUN bitnami-pkg install ruby-2.4.4-0 --checksum 8623ed8b7963916ff7f5ecf56c62ce3c144a1d11e56767500d0034c8e4f7e17c
RUN bitnami-pkg unpack postgresql-client-9.6.9-0 --checksum e4e745c0f5020041c6b2f0c249c8e760a5724d2f64c48b712dc22bb714a7eea4
RUN bitnami-pkg install git-2.18.0-0 --checksum 1eb754ba867f732f706db6d202481ad968be9cb4def0421770ed1c52484a2e8e
RUN bitnami-pkg unpack discourse-sidekiq-2.0.2-0 --checksum f763f46b6fa47834fac0a3dd3e9be514cb5ff09c596617ee929c1e143a309647
RUN bitnami-pkg unpack discourse-2.0.2-0 --checksum 5fb04cfe416415b1a52f4bedbb31cdae570bfc949171ae2e4156a4795e5882b2

COPY rootfs /
ENV BITNAMI_APP_NAME="discourse" \
    BITNAMI_IMAGE_VERSION="2.0.2-ol-7-r3" \
    DISCOURSE_EMAIL="user@example.com" \
    DISCOURSE_HOST="127.0.0.1" \
    DISCOURSE_PASSWORD="bitnami123" \
    DISCOURSE_PORT="3000" \
    DISCOURSE_POSTGRESQL_NAME="bitnami_application" \
    DISCOURSE_POSTGRESQL_PASSWORD="bitnami1" \
    DISCOURSE_POSTGRESQL_USERNAME="bn_discourse" \
    DISCOURSE_SITE_NAME="My site!" \
    DISCOURSE_USERNAME="user" \
    PATH="/opt/bitnami/ruby/bin:/opt/bitnami/postgresql/bin:/opt/bitnami/git/bin:$PATH" \
    POSTGRESQL_CLIENT_CREATE_DATABASE_NAME="" \
    POSTGRESQL_CLIENT_CREATE_DATABASE_PASSWORD="" \
    POSTGRESQL_CLIENT_CREATE_DATABASE_USERNAME="" \
    POSTGRESQL_HOST="postgresql" \
    POSTGRESQL_PORT_NUMBER="5432" \
    POSTGRESQL_ROOT_PASSWORD="" \
    POSTGRESQL_ROOT_USER="postgres" \
    REDIS_HOST="redis" \
    REDIS_PASSWORD="" \
    REDIS_PORT_NUMBER="6379" \
    SMTP_HOST="" \
    SMTP_PASSWORD="" \
    SMTP_PORT="" \
    SMTP_TLS="true" \
    SMTP_USER=""

EXPOSE 3000

ENTRYPOINT ["/app-entrypoint.sh"]
CMD ["nami","start","--foreground","discourse"]