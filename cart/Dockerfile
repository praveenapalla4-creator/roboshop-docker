#idhi just required installations kosam use chesthunnam-1
FROM node:20.19.5-alpine3.22 AS build
WORKDIR /opt/server
COPY package.json .
COPY *.js .
# this may add extra cache memory
RUN npm install  


FROM node:20.19.5-alpine3.22 
# Create a group and user
WORKDIR /opt/server
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop && \
 chown -R roboshop:roboshop /opt/server
EXPOSE 8080
LABEL com.project="roboshop" \
      component= "user" \
      created_by="cart"
ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080"
#kavlsina content ni final image ki copy chesthunnam from 1
COPY --from=build --chown=roboshop:roboshop /opt/server /opt/server
USER roboshop
CMD ["node", "server.js"]
ENTRYPOINT ["node"]


# FROM node:20
# WORKDIR /opt/server
# EXPOSE 8080
# COPY package.json .
# COPY *.js .
# RUN npm install
# ENV REDIS_HOST="redis"\
#     CATALOGUE_HOST="catalogue"\
#     CATALOGUE_PORT="8080"
# CMD ["node", "server.js"]
