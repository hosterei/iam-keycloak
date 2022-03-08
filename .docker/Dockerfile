FROM quay.io/keycloak/keycloak-x:16.1.1 as builder

ENV KC_METRICS_ENABLED=true
ENV KC_FEATURES=token-exchange
RUN /opt/keycloak/bin/kc.sh build

FROM quay.io/keycloak/keycloak-x:16.1.1
COPY --from=builder /opt/keycloak/lib/quarkus/ /opt/keycloak/lib/quarkus/
WORKDIR /opt/keycloak

ENTRYPOINT ["/opt/keycloak/bin/kc.sh", "start"]