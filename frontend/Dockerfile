FROM node:9.9.0

ARG NG_CLI_VERSION=1.7.3
ARG USER_HOME_DIR="/tmp"
ARG APP_DIR="/app"
ARG USER_ID=1000

ENV NPM_CONFIG_LOGLEVEL warn
#angular-cli rc0 crashes with .angular-cli.json in user home
ENV HOME "$USER_HOME_DIR"

# npm 5 uses different userid when installing packages, as workaround su to node when installing
# see https://github.com/npm/npm/issues/16766
RUN set -xe \
	&& mkdir -p /tmp \
    && chown 1000 /tmp \
    && chmod a+rw /tmp \
    && chown -R node /usr/local/lib /usr/local/include /usr/local/share /usr/local/bin \
    && (cd "/tmp"; su node -c "npm install -g @angular/cli@1.7.3; npm install -g yarn; npm cache clean --force")

#not declared to avoid anonymous volume leak
WORKDIR /app
RUN chown -R 1000 /app
EXPOSE 4200

USER 1000
RUN git clone https://github.com/lolobored/plex-on-the-go-frontend.git

WORKDIR /app/plex-on-the-go-frontend

RUN npm install

CMD ["ng", "serve", "--host", "0.0.0.0", "--disable-host-check"]