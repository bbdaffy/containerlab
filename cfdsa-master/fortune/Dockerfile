## build start ##
FROM node:latest

# define environment variables needed by the application
ENV APP_PORT=5000 APP_DIR=/fortune

# create APP_DIR and cd inside
WORKDIR ${APP_DIR}

# copy files to APP_DIR
ADD main.js .
ADD package.json .
# directory must have a target name and the copying is recursive
ADD public public
ADD views views

# install libraries from package.json
RUN npm install
## build end ##

## execution start
# container will listen to the exposed port i.e. APP_PORT. This is only for documentation. 
# Application has to support the port.
EXPOSE ${APP_PORT}

HEALTHCHECK --interval=60s --timeout=5s --retries=3 CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1

ENTRYPOINT [ "node", "main.js" ]
# entrypoint is fixed. commandline parameters can be added in further by using CMD. E.g.
# CMD [ "3000" ]
## execution end