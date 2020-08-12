FROM registry.redhat.io/rhacm1-tech-preview/coredns-rhel8:v1.0.1-2
USER root
LABEL maintainer="Romain Chantereau"
# Copy config
COPY Corefile /Corefile
COPY db.example.org /db.example.org
# Start the service
EXPOSE 1053/udp 53/udp
ENTRYPOINT ["/coredns"]
