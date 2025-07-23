FROM node:20-alpine3.21 as builder
WORKDIR /opt/server
COPY . .
RUN npm install --unsafe-perm

FROM node:20-alpine3.21
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
ENV MONGO="true" \
    REDIS_URL="redis://redis:6379" \
    MONGO_URL="mongodb://mongodb:27017/users"
WORKDIR /opt/server
USER roboshop
COPY --from=builder /opt/server /opt/server
CMD ["node", "server.js"]

# FROM node:20-alpine
# RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
# WORKDIR /opt/server
# COPY . .
# RUN chown -R roboshop:roboshop /opt/server
# USER roboshop
# RUN npm install --unsafe-perm
# ENV MONGO="true" \
#     REDIS_URL="redis://redis:6379" \
#     MONGO_URL="mongodb://mongodb:27017/users"
# CMD ["node", "server.js"]

