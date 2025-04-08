# Use Ubuntu 18.04 as the base image
FROM ubuntu:18.04

# Set the environment variables to non-interactive to prevent prompts during installation
ENV DEBIAN_FRONTEND=noninteractive

# Update and install dependencies
RUN apt-get update && apt-get install -y \
    git \
    gawk \
    qpdf \
    flex \
    bison \
    dpkg \
    xxd \
    && apt-get clean

# Add i386 architecture support (only needed for x86_64 systems)
RUN dpkg --add-architecture i386 \
    && apt-get update

# Install 32-bit libraries for x86_64 architecture
RUN apt-get install -y \
    libc6:i386 \
    libncurses5:i386 \
    libstdc++6:i386 \
 && apt-get clean

# Set up the working directory
WORKDIR /workspace

# Copy the nexmon repository from the local system into the container
# Change the path below to the location where you have the nexmon repo on your host machine
COPY ./ /workspace/nexmon

# Set the working directory to where nexmon was copied
WORKDIR /workspace/nexmon

# Install additional build tools and perform setup as needed
# RUN make all or any other commands you need to execute for setup
RUN apt-get install -y \
    tree \
    nano \
    make

# Expose any ports you may need (optional)
# EXPOSE <port>

# Start a shell when the container runs (optional, you can modify this as needed)
CMD ["/bin/bash"]
