FROM ortussolutions/commandbox:jdk21-snapshot

ENV BOX_SERVER_APP_CFENGINE=boxlang@1.0.0-beta11+15

RUN box upgrade --force --latest

RUN ${BUILD_DIR}/util/warmup-server.sh

RUN box install commandbox-boxlang,bx-compat,bx-esapi,bx-pdf

COPY ./app /app

COPY ./.github/build/server.json /app/server.json

RUN /bin/bash -c "$(curl -fsSL https://downloads.ortussolutions.com/ortussolutions/boxlang/install-boxlang.sh)"

RUN boxlang --home /usr/local/lib/serverHome/WEB-INF/boxlang compile --source /app/ --target /app/ --basePath /app