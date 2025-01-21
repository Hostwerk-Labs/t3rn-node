# Use an official Ubuntu as a parent image
FROM ubuntu:latest

RUN apt update && \
    apt-get -fy install \
    curl \
    wget

# Create and navigate to t3rn directory
RUN mkdir t3rn
WORKDIR t3rn

# Download latest release
RUN curl -s https://api.github.com/repos/t3rn/executor-release/releases/latest | \
    grep -Po '"tag_name": "\K.*?(?=")' | \
    xargs -I {} wget https://github.com/t3rn/executor-release/releases/download/{}/executor-linux-{}.tar.gz

# Extract the archive
RUN tar -xzf executor-linux-*.tar.gz

# Navigate to the executor binary location
ENTRYPOINT ["/t3rn/executor/executor/bin/executor"]
