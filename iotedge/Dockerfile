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

# Install balena & create docker "symlink" 
RUN apt-get install -y curl
RUN curl -sfL https://balena.io/install.sh | sh
COPY docker /usr/local/bin
RUN chmod +x /usr/local/bin/docker

# Install azure-iot-edge-runtime-ctl
RUN pip3 install -U azure-iot-edge-runtime-ctl

CMD ["/bin/sh", "/app/startEdge.sh"]
