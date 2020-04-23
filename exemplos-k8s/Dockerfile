FROM node:lts

WORKDIR /app/website

EXPOSE 3000 3000
COPY ./docs /app/docs
COPY ./website /app/website
RUN yarn install

CMD ["yarn", "start"]
