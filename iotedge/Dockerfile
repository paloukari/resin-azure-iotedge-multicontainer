FROM resin/armv7hf-debian

# Install Python and pip
RUN apt-get update
RUN apt-get install -y --no-install-recommends gcc python3 python3-pip 
RUN apt-get install -y --no-install-recommends libffi-dev 
RUN apt-get install -y --no-install-recommends libssl-dev
RUN apt-get install -y --no-install-recommends python3-dev 
RUN pip3 install --upgrade setuptools pip
RUN pip install cffi
RUN easy_install -U setuptools


COPY ./app /app
COPY ./azure-iotedge-runtime /azure-iotedge-runtime

# Install azure-iot-edge-runtime-ctl
RUN pip3 install -U azure-iot-edge-runtime-ctl

# Install balena & create docker "symlink" 
RUN apt-get install -y curl

RUN apt-get install --only-upgrade tar

RUN curl -sL https://github.com/resin-os/balena/releases/download/17.06-rev1/balena-17.06-rev1-armv7.tar.gz | tar xzv -C /usr/local/bin --strip-components=1

COPY docker /usr/local/bin
RUN chmod +x /usr/local/bin/docker

CMD ["/bin/sh", "/app/startEdge.sh"]
