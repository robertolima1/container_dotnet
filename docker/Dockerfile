FROM ubuntu:20.04

RUN apt update && \
    DEBIAN_FRONTEND="noninteractive" apt install -y curl git vim wget doxygen graphviz

# Install .Net 6.0
RUN wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
RUN dpkg -i packages-microsoft-prod.deb && \
    rm packages-microsoft-prod.deb

RUN apt-get update && \
    apt-get install -y apt-transport-https && \
    DEBIAN_FRONTEND="noninteractive" apt-get install -y dotnet-sdk-6.0 dotnet-runtime-6.0

RUN apt-get update && \
    DEBIAN_FRONTEND="noninteractive" apt-get install -y aspnetcore-runtime-6.0


# Instal Mono CLI
RUN apt update && \
    apt install -y  gnupg ca-certificates && \
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF && \
    echo "deb https://download.mono-project.com/repo/ubuntu stable-focal main" |  tee /etc/apt/sources.list.d/mono-official-stable.list && \
    apt update && \
    apt install -y  mono-devel


# Install Nuget CLI
    RUN apt update && \
        curl -o /usr/local/bin/nuget.exe https://dist.nuget.org/win-x86-commandline/latest/nuget.exe && \
        alias nuget="mono /usr/local/bin/nuget.exe"


      
# Install Azure Artifacts Credential Provider

  RUN apt update && \
      wget -qO- https://aka.ms/install-artifacts-credprovider.sh | bash && \
      sh -c "$(curl -fsSL https://aka.ms/install-artifacts-credprovider.sh)"

    
