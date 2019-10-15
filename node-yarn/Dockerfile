FROM node:12.10.0-alpine

RUN apk update && apk add ca-certificates

RUN apk add curl && \
   apk add bash

RUN echo @edge http://nl.alpinelinux.org/alpine/edge/community >> /etc/apk/repositories \
   && echo @edge http://nl.alpinelinux.org/alpine/edge/main >> /etc/apk/repositories \
   && apk add --no-cache \
   chromium firefox-esr \
   xvfb dbus-x11 \
   nss \
   freetype \
   harfbuzz \
   ttf-freefont \
   chromium-chromedriver \
   && rm -rf /var/cache/* \
   && mkdir /var/cache/apk

ENV CHROME_BIN=/usr/bin/chromium-browser \
   CHROME_PATH=/usr/lib/chromium/ \
   CHROMIUM_BIN=/usr/bin/chromium-browser

RUN npm install --global yarn

RUN yarn global add jest

ENV CI_ALPINE_BUILD=true

CMD ["/bin/sh"]