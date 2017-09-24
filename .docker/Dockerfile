FROM rocketchat/base:4

USER rocketchat

VOLUME /app/uploads

WORKDIR /app/bundle
RUN curl https://install.meteor.com/ | /bin/sh
ADD . /app/bundle 
RUN ./example-build-run.sh

# needs a mongoinstance - defaults to container linking with alias 'mongo'
ENV DEPLOY_METHOD=docker \
    NODE_ENV=production \
    MONGO_URL=mongodb://mongo:27017/rocketchat \
    HOME=/tmp \
    PORT=3000 \
    ROOT_URL=http://localhost:3000 \
    Accounts_AvatarStorePath=/app/uploads

EXPOSE 3000

CMD ["node", "main.js"]
