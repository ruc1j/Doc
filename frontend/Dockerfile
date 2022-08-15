FROM node:16.15.0-alpine

ENV LANG C.UTF-8
ENV TZ Asia/Tokyo

WORKDIR /usr/src/app/next
ADD /frontend/app/package.json package.json

RUN yarn add -D prettier \
    eslint-config-prettier \
    eslint \
    @typescript-eslint/parser \
    @typescript-eslint/eslint-plugin \
    axios \
    swr \
    @mui/material \
    @mui/lab \
    @emotion/babel-plugin \
    @emotion/react \
    @emotion/styled \
    react \
    react-dom \
    react-hook-form 


# サーバーの起動(nextアプリを作成した後、有効化する)。コンテナが起動してから30秒後くらいに起動。
# CMD ["yarn" "dev"]