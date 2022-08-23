FROM networkstatic/iperf3

RUN apt update && apt install sysstat iproute2 -y --no-install-recommends && \
    rm -rf /var/lib/apt/lists/*

