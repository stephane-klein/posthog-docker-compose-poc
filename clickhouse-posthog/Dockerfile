FROM alpine

RUN apk add curl

RUN curl -L https://github.com/PostHog/posthog/archive/refs/tags/1.32.0.tar.gz | tar zxv

FROM yandex/clickhouse-server:21.6.5

COPY --from=0 /posthog-1.32.0/ee/idl/ /idl/
COPY --from=0 /posthog-1.32.0/docker/clickhouse/docker-entrypoint-initdb.d /docker-entrypoint-initdb.d
COPY --from=0 /posthog-1.32.0/docker/clickhouse/config.xml                 /etc/clickhouse-server/config.xml
COPY --from=0 /posthog-1.32.0/docker/clickhouse/users.xml                  /etc/clickhouse-server/users.xml
