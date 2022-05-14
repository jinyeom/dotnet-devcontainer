ARG VERSION=${VERSION}
FROM mcr.microsoft.com/dotnet/sdk:$VERSION AS dev

# Install packages
RUN apt-get update && \
    apt-get install -y sudo git openssh-client && \
    apt-get autoremove -y && \
    apt-get clean -y && \
    rm -rf /var/lib/apt/lists/*

ARG USERNAME=${USERNAME}
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Create the user
RUN groupadd --gid $USER_GID $USERNAME && \
    useradd --uid $USER_UID --gid $USER_GID -m $USERNAME && \
    echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME && \
    chmod 0440 /etc/sudoers.d/$USERNAME

USER $USERNAME

CMD [ "/bin/bash" ]