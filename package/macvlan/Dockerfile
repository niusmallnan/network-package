FROM rancher/agent-base:v0.3.0
ENV CNI v0.3.0
ENV RANCHER_CNI_DRIVER v0.1.0
ENV RANCHER_CNI_MACVLAN v0.1.0
ENV RANCHER_CNI_IPAM v0.2.1

ADD https://github.com/rancher/cni-driver/releases/download/${RANCHER_CNI_DRIVER}/rancher-cni-driver-amd64-${RANCHER_CNI_DRIVER}.tar.gz /

RUN mkdir -p /opt/cni/bin /etc/cni/net.d \
    && curl -sfSL https://github.com/containernetworking/cni/releases/download/${CNI}/cni-${CNI}.tgz | tar xvzf - -C /tmp ./loopback \
    && curl -sfSL https://github.com/rancher/rancher-cni-ipam/releases/download/${RANCHER_CNI_IPAM}/rancher-cni-ipam-${RANCHER_CNI_IPAM}.tar.gz | tar xvzf - -C /tmp \
    && mv /tmp/* /opt/cni/bin

COPY setup-md-gw.sh /usr/bin/

CMD ["sleep", "infinity"]
