FROM centos:6
MAINTAINER Nan Liu <nan.liu@gmail.com>

ARG BUILD_DATE
ARG SNAP_VERSION=latest

ENV SNAP_VERSION=${SNAP_VERSION}
ENV SNAP_TRUST_LEVEL=0
ENV SNAP_LOG_LEVEL=1
ENV SNAP_URL=https://s3-us-west-2.amazonaws.com/snap.ci.snap-telemetry.io

LABEL vendor="Intelsdi-X" \
      name="Snap Centos 6" \
      license="Apache 2.0" \
      build-date=$BUILD_DATE \
      io.snap-telemetry.snap.version=$SNAP_VERSION \
      io.snap-telemetry.snap.version.is-beta=

EXPOSE 8181

ADD ${SNAP_URL}/snap/${SNAP_VERSION}/linux/x86_64/snapd  /opt/snap/bin/snapd
ADD ${SNAP_URL}/snap/${SNAP_VERSION}/linux/x86_64/snapctl  /opt/snap/bin/snapctl
COPY init_snap /usr/local/bin/init_snap
COPY snapd.conf /etc/snap/snapd.conf

CMD /usr/local/bin/init_snap && /opt/snap/bin/snapd -t ${SNAP_TRUST_LEVEL} -l ${SNAP_LOG_LEVEL} -o ''
