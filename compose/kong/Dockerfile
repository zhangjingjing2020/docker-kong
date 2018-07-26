FROM kong

# get ContainerPilot release
ENV CONTAINERPILOT_VERSION 2.7.8
RUN export CP_SHA1=09158be44c3e887244581d4d019748df9fcfa93c \
    && curl -Lso /tmp/containerpilot.tar.gz \
         "https://github.com/joyent/containerpilot/releases/download/${CONTAINERPILOT_VERSION}/containerpilot-${CONTAINERPILOT_VERSION}.tar.gz" \
    && echo "${CP_SHA1}  /tmp/containerpilot.tar.gz" | sha1sum -c \
    && tar zxf /tmp/containerpilot.tar.gz -C /bin \
    && rm /tmp/containerpilot.tar.gz

# add ContainerPilot configuration
COPY containerpilot.json /etc/containerpilot.json
ENV CONTAINERPILOT=file:///etc/containerpilot.json

CMD /bin/containerpilot kong start --run-migrations

EXPOSE 8000 8443 8001 7946
