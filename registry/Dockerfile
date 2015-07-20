FROM registry:0.9.1

#https://github.com/docker/docker-registry/issues/892
ENV GUNICORN_OPTS ["--preload"]

RUN adduser --system registry \
&& addgroup registry \
&& chown -R registry:registry /docker-registry

USER registry

#https://github.com/docker/docker-registry/issues/915
WORKDIR /docker-registry

CMD ["docker-registry"]
