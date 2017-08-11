FROM node:8

RUN mkdir -p /usr/src/app
RUN git clone https://github.com/houndci/remark /usr/src/app \
    && cd /usr/src/app \
    && git reset --hard b0b2c36920ae3d5a5d06ca90d11f6b3c9f9b7b2f
WORKDIR /usr/src/app

RUN npm install

CMD npm start
