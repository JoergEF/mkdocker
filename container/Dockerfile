#build stage
FROM python:3-alpine AS build
RUN apk add build-base
COPY ./mkdocs/ /mkdocs/
WORKDIR /mkdocs/
RUN pip install mkdocs mkdocs-material
RUN mkdocs build

#web server stage
FROM nginx:alpine
COPY --from=0 /mkdocs/site/ /usr/share/nginx/html
EXPOSE 80