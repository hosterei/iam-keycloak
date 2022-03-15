FROM quay.io/keycloak/keycloak:17.0.0 as builder

ENV KC_METRICS_ENABLED=true
ENV KC_FEATURES=token-exchange
ENV KC_HOSTNAME_PATH=/auth
ENV KC_HTTP_RELATIVE_PATH=/auth
RUN /opt/keycloak/bin/kc.sh build --db=postgres

FROM quay.io/keycloak/keycloak:17.0.0
COPY --from=builder /opt/keycloak/lib/quarkus/ /opt/keycloak/lib/quarkus/
WORKDIR /opt/keycloak

ENTRYPOINT ["/opt/keycloak/bin/kc.sh", "start"]