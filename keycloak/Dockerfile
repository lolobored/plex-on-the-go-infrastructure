FROM jboss/keycloak:4.0.0.Final

ADD realm-export.json /opt/jboss/

RUN sh -c "/opt/jboss/keycloak/bin/standalone.sh -Dkeycloak.migration.action=import -Dkeycloak.migration.provider=singleFile -Dkeycloak.migration.file=/opt/jboss/realm-export.json -Dkeycloak.migration.strategy=OVERWRITE_EXISTING -Dkeycloak.migration.realmName=plex &" && sleep 45 
