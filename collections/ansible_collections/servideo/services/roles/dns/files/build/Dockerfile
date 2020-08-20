FROM registry.redhat.io/rhacm1-tech-preview/coredns-rhel8:v1.0.1-2
USER root
LABEL maintainer="Romain Chantereau"
# Copy config
COPY Corefile /Corefile
COPY db/* /
# Start the service
EXPOSE 53/udp 53/tcp
ENTRYPOINT ["/coredns"]
