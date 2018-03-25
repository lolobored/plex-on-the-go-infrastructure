FROM gradle:4.6.0-jdk8

USER root
WORKDIR /app
RUN set -xe \
	&& chmod 777 . \
	&& git clone https://github.com/lolobored/plex-on-the-go.git

WORKDIR /app/plex-on-the-go

RUN gradle clean build

EXPOSE 8080


CMD ["gradle", "bootRun"]
