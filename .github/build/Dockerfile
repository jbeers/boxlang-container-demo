FROM ortussolutions/commandbox:jdk21-snapshot

ENV BOX_SERVER_APP_CFENGINE=boxlang@1.0.0-beta11+15

RUN box upgrade --force --latest

RUN ${BUILD_DIR}/util/warmup-server.sh

RUN box install commandbox-boxlang,bx-compat,bx-esapi,bx-pdf

COPY ./app /app

COPY ./.github/build/server.json /app/server.json


