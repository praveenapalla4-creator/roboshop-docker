#idhi just required installations kosam use chesthunnam-1
FROM node:20.19.5-alpine3.22 AS build
WORKDIR /opt/server
COPY package.json .
COPY *.js .
# this may add extra cache memory
RUN npm install  


FROM node:20.19.5-alpine3.22 
# Create a group and user
RUN addgroup -S roboshop && adduser -S roboshop -G appgroup
WORKDIR /opt/server
#kavlsina content ni final image ki copy chesthunnam from 1
COPY --from=build  /opt/server /opt/server
ENV MONGO="true"\
    MONGO_URL="mongodb://mongodb:27017/catalogue"
USER roboshop
RUN chown -R roboshop:roboshop /opt/server
CMD ["node", "server.js"]




# FROM node:20.19.5-alpine3.22 
# WORKDIR /opt/server
# COPY package.json .
# COPY *.js .

# # this may add extra cache memory
# RUN npm install
# ENV MONGO="true"\
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node", "server.js"]



# FROM node:20
# WORKDIR /opt/server
# COPY package.json .
# COPY *.js .
# RUN npm install
# ENV MONGO="true"\
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node", "server.js"]
