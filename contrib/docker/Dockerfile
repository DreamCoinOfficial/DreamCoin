FROM debian:jessie
MAINTAINER pavik - https://github.com/pavik

ENV DREM_VERSION=1.0.3 \
 DREM_USER=drem

ENV DREM_URL=https://github.com/DreamPay/DreamPay/releases/download/v$DREM_VERSION/drem-$DREM_VERSION-x86_64-linux-gnu.tar.gz \
 DREM_CONF=/home/$DREM_USER/.DreamPay/DreamPay.conf \
 DREM_CONF_URL=https://raw.githubusercontent.com/DreamPay/DreamPay/master/DreamPay.conf

RUN apt-get -qq update && \
apt-get install -yq wget ca-certificates pwgen && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
wget $DREM_URL -O /tmp/drem.tar.gz && \
mkdir -p /opt && \
cd /opt && \
tar xvzf /tmp/drem.tar.gz && \
rm /tmp/drem.tar.gz && \
ln -sf drem-$DREM_VERSION drem && \
ln -sf /opt/drem/bin/dremd /usr/local/bin/dremd && \
ln -sf /opt/drem/bin/drem-cli /usr/local/bin/drem-cli && \
ln -sf /opt/drem/bin/drem-tx /usr/local/bin/drem-tx && \
adduser --uid 1000 --system ${DREM_USER} && \
mkdir -p /home/${DREM_USER}/.DreamPay/ && \
chown -R ${DREM_USER} /home/${DREM_USER} && \
echo "success: $DREM_CONF"

USER drem
RUN wget $DREM_CONF_URL -O $DREM_CONF && \
    sed -i -e 's/\*your$username\*/drem/g' ${DREM_CONF} && \
    sed -i -e 's/\*your$password\*/'`pwgen 32 1`'/g' ${DREM_CONF} && \
    echo "Success"

EXPOSE 51572
VOLUME ["/home/drem/.DreamPay"]
WORKDIR /home/drem

ENTRYPOINT ["/usr/local/bin/dremd"]