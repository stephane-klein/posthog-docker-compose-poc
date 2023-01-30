FROM alpine

RUN apk add curl

RUN curl -L https://github.com/PostHog/posthog/archive/refs/tags/1.40.0.tar.gz | tar zxv

FROM clickhouse/clickhouse-server:22.3

# this file list come from https://github.com/PostHog/posthog/blob/master/docker-compose.yml#L26
COPY --from=0 /posthog-1.40.0/posthog/idl/ /idl/
COPY --from=0 /posthog-1.40.0/docker/clickhouse/docker-entrypoint-initdb.d /docker-entrypoint-initdb.d
COPY --from=0 /posthog-1.40.0/docker/clickhouse/config.xml                 /etc/clickhouse-server/config.xml
COPY --from=0 /posthog-1.40.0/docker/clickhouse/users.xml                  /etc/clickhouse-server/uselolog-g-serverl

COPY ./log-server-config.xml                  /etc/clickhouse-server/config.d/
COPY ./log-users-config.xml                  /etc/clickhouse-server/users.d/
