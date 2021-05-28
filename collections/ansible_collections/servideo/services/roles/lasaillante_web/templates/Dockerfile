FROM registry.connect.redhat.com/haproxytech/haproxy
USER root
LABEL maintainer="Romain Chantereau"
# Copy config
COPY haproxy.cfg /etc/haproxy/haproxy.cfg
# Start the service
EXPOSE {% for item in port_mapping %}{{ item.exposed_port }}/{{ item.protocol }} {% endfor %}

CMD ["/usr/local/sbin/haproxy","-f","/etc/haproxy/haproxy.cfg"]
