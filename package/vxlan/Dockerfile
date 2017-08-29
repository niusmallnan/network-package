FROM rancher/agent-base:v0.3.0
ENV CNI v0.3.0
ENV RANCHER_CNI_BRIDGE v0.6.0
ENV RANCHER_CNI_IPAM v0.1.2
ENV RANCHER_VXLAN v0.1.0

RUN mkdir -p /opt/cni/bin /etc/cni/net.d \
    && curl -sfSL https://github.com/containernetworking/cni/releases/download/${CNI}/cni-${CNI}.tgz | tar xvzf - -C /tmp ./loopback \
    && curl -sfSL https://github.com/rancher/rancher-cni-ipam/releases/download/${RANCHER_CNI_IPAM}/rancher-cni-ipam-${RANCHER_CNI_IPAM}.tar.gz | tar xvzf - -C /tmp \
    && curl -sfSL https://github.com/rancher/rancher-cni-bridge/releases/download/${RANCHER_CNI_BRIDGE}/rancher-cni-bridge-${RANCHER_CNI_BRIDGE}.tar.gz | tar xvzf - -C /tmp \
    && curl -sfSL https://github.com/rancher/vxlan/releases/download/${RANCHER_VXLAN}/rancher-vxlan-amd64-${RANCHER_VXLAN}.tar.gz | tar xvzf - -C /tmp \
    && mv /tmp/rancher-cni-bridge /tmp/rancher-bridge \
    && mv /tmp/rancher-vxlan /usr/bin \
    && mv /tmp/* /opt/cni/bin

CMD ["rancher-vxlan"]
