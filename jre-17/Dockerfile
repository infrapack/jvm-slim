FROM amazoncorretto:17-alpine-jdk as corretto-jdk

# required for strip-debug to work
RUN apk add --no-cache binutils

# Build small JRE image
RUN $JAVA_HOME/bin/jlink \
	--verbose \
	--add-modules java.base,java.desktop,java.naming,java.net.http,java.sql,java.xml,jdk.crypto.cryptoki,jdk.crypto.ec,jdk.naming.dns,jdk.naming.rmi,jdk.net,jdk.unsupported,jdk.zipfs \
	--strip-debug \
	--no-man-pages \
	--no-header-files \
	--compress=2 \
	--output /customjre

# main app image
FROM alpine:3.18
ENV JAVA_HOME=/jre
ENV PATH="${JAVA_HOME}/bin:${PATH}"

# copy JRE from the base image
COPY --from=corretto-jdk /customjre $JAVA_HOME

# Add app user
ARG APPLICATION_USER=appuser
RUN adduser --no-create-home -u 1000 -D $APPLICATION_USER

# Configure working directory
RUN mkdir /app && \
	chown -R $APPLICATION_USER /app

USER 1000
WORKDIR /app