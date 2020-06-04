FROM google/dart:2

# Avoid warnings by switching to noninteractive
ENV DEBIAN_FRONTEND=noninteractive

# Add bin location to path
ENV PATH="$PATH":"/root/.pub-cache/bin"

# Add flutter to path
ENV PATH="/flutter/bin:${PATH}"

# This Dockerfile adds a non-root user with sudo access. Use the "remoteUser"
# property in devcontainer.json to use it. On Linux, the container user's GID/UIDs
# will be updated to match your local UID/GID (when using the dockerFile property).
# See https://aka.ms/vscode-remote/containers/non-root-user for details.
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Configure apt and install packages
RUN apt-get update \
    && apt-get -y install --no-install-recommends apt-utils dialog 2>&1 \
    #
    # Verify git, process tools, lsb-release (common in install instructions for CLIs) installed
    && apt-get -y install git openssh-client less iproute2 procps lsb-release \
    #
    # Verify flutter dependencies installed
    unzip xz-utils zip libglu1-mesa \
    #
    # Create a non-root user to use if preferred - see https://aka.ms/vscode-remote/containers/non-root-user.
    && groupadd --gid $USER_GID $USERNAME \
    && useradd -s /bin/bash --uid $USER_UID --gid $USER_GID -m $USERNAME \
    # [Optional] Add sudo support for the non-root user
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME\
    && chmod 0440 /etc/sudoers.d/$USERNAME \
    #
    # Clean up
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/* \
    # 
    # 
    # Flutter:
    # Install
    && git clone https://github.com/flutter/flutter.git /flutter \
    # Disable analytics reports
    && flutter config --no-analytics \
    # Enable web
    && flutter channel beta \
    && flutter upgrade \
    && flutter config --enable-web

# Switch back to dialog for any ad-hoc use of apt-get
ENV DEBIAN_FRONTEND=dialog
