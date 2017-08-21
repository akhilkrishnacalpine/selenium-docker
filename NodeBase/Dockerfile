FROM siliconvalleyclouldit/seleniumbase:latest

USER root

RUN apt-get update -qqy \
  && apt-get -qqy install \
    locales \
    xvfb \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/*

USER seluser

COPY entry_point.sh \
  functions.sh \
    /opt/bin/
RUN sudo chmod +x /opt/bin/entry_point.sh \
    && sudo chmod +x /opt/bin/functions.sh

ENV SCREEN_WIDTH 1360
ENV SCREEN_HEIGHT 1020
ENV SCREEN_DEPTH 24
ENV DISPLAY :99.0


# As integer, maps to "maxInstances"
ENV NODE_MAX_INSTANCES 1
# As integer, maps to "maxSession"
ENV NODE_MAX_SESSION 1
# As integer, maps to "port"
ENV NODE_PORT 5555
# In milliseconds, maps to "registerCycle"
ENV NODE_REGISTER_CYCLE 5000
# In milliseconds, maps to "nodePolling"
ENV NODE_POLLING 5000
# In milliseconds, maps to "unregisterIfStillDownAfter"
ENV NODE_UNREGISTER_IF_STILL_DOWN_AFTER 60000
# As integer, maps to "downPollingLimit"
ENV NODE_DOWN_POLLING_LIMIT 2
# As string, maps to "applicationName"
ENV NODE_APPLICATION_NAME ""

ENV DBUS_SESSION_BUS_ADDRESS=/dev/null

CMD ["/opt/bin/entry_point.sh"]
