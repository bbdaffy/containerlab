## build start
FROM node:latest

ENV DB_HOST=nwdb DB_PORT=3306 \
 DB_USER=root DB_PASSWORD=changeit \
 APP_PORT=3000 APP_DIR=/app

# create APP_DIR and cd inside
WORKDIR ${APP_DIR}

# copy files to APP_DIR
ADD main.js .
ADD package.json .
ADD public public
ADD views views
ADD config config

# install libraries from package.json
RUN npm install
## build end ##

## execution start
EXPOSE ${APP_PORT}

HEALTHCHECK --interval=30s --timeout=30s --retries=3 \
    CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1

ENTRYPOINT [ "node", "main.js" ]
## execution end
