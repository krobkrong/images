FROM alpine:edge

RUN echo @edge http://nl.alpinelinux.org/alpine/edge/community >> /etc/apk/repositories \
   && echo @edge http://nl.alpinelinux.org/alpine/edge/testing >> /etc/apk/repositories \
   && echo @edge http://nl.alpinelinux.org/alpine/edge/main >> /etc/apk/repositories \
   && apk update \
   && apk upgrade \
   && apk add ca-certificates \
   && apk add --no-cache \
              firefox@edge \
              chromium@edge \
              chromium-chromedriver@edge \
              nodejs \
              jq \
              curl \
              bash \
   && rm -rf /var/cache/* \
   && mkdir /var/cache/apk

COPY geckodriver.sh geckodriver.sh
RUN sh geckodriver.sh

ENV CHROME_BIN=/usr/bin/chromium-browser \
    CHROME_PATH=/usr/lib/chromium/ \
    CHROMIUM_BIN=/usr/bin/chromium-browser

RUN curl -o- -L https://yarnpkg.com/install.sh | bash \
    && ln -s $HOME/.yarn/bin/yarn /usr/bin/yarn

RUN yarn global add jest

ENV CI_ALPINE_BUILD=true

CMD ["/bin/sh"]