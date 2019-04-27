FROM node:8.16.0-alpine

RUN apk update && apk add ca-certificates

RUN apk add yarn

RUN yarn global add jest

CMD ["/bin/sh"]