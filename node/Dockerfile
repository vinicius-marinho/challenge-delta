FROM node AS source
RUN mkdir /app/
ADD ./app /app/
WORKDIR /app/
RUN npm install

#Multi stage build so the image can be as minimal as possible

FROM node:alpine
ARG APP_VERSION=V1.1
LABEL com.hurb.version=${APP_VERSION}
COPY --from=source /app/ /app/
WORKDIR /app/
EXPOSE 8888
ENTRYPOINT [ "node", "server.js" ]
