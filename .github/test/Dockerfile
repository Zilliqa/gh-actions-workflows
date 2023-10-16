FROM ubuntu:22.04

# Set environment variables to avoid interactive prompts during installation
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get -y update && \
    apt-get upgrade -y && \
    apt-get install -y \
        curl \
        git \
        unzip \
        wget

CMD ["bash"]