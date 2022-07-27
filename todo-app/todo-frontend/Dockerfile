FROM node:16 AS test-stage

WORKDIR /usr/src/app

COPY . .

RUN npm ci

RUN CI=true npm test


FROM test-stage AS build-stage

WORKDIR /usr/src/app

COPY . .

RUN npm ci

ARG REACT_APP_BACKEND_URL
ENV REACT_APP_BACKEND_URL=$REACT_APP_BACKEND_URL

RUN npm run build

RUN npm install -g serve

CMD ["serve", "build"]