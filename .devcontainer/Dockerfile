# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.234.0/containers/debian/.devcontainer/base.Dockerfile

# [Choice] Debian version (use bullseye on local arm64/Apple Silicon): bullseye, buster
ARG VARIANT="buster"
FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

# ** [Optional] Uncomment this section to install additional packages. **
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

RUN apt update && apt upgrade -y

# install cobol development environment
RUN apt install -y gnucobol

# install development util.
RUN apt install -y mlocate vim

# install .net runtime for using oracle.oracledevtools vscode extension.
RUN wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
RUN dpkg -i packages-microsoft-prod.deb
RUN rm packages-microsoft-prod.deb
RUN apt update && apt-get install -y dotnet-runtime-6.0

# install sqlcl for connect db container 
RUN su - vscode -c 'wget https://download.oracle.com/otn_software/java/sqldeveloper/sqlcl-21.2.0.174.2245.zip'
RUN su - vscode -c 'unzip sqlcl-21.*.zip'
RUN su - vscode -c 'mv /home/vscode/sqlcl/bin/sql /home/vscode/sqlcl/bin/sqlcl'
RUN su - vscode -c 'rm sqlcl-21.*.zip'
RUN su - vscode -c 'echo export PATH=\$PATH:/home/vscode/sqlcl/bin >> ~/.bashrc'
RUN apt install -y openjdk-11-jre

# create function for sample
COPY db_sample.sh .
RUN chmod u+x ./db_sample.sh
RUN ./db_sample.sh
RUN rm db_sample.sh

# download scheme.spy
RUN su - vscode -c 'wget https://github.com/schemaspy/schemaspy/releases/download/v6.1.0/schemaspy-6.1.0.jar'
RUN su - vscode -c 'mv schemaspy-*.jar schemaspy.jar'
RUN su - vscode -c 'wget https://download.oracle.com/otn-pub/otn_software/jdbc/215/ojdbc8-full.tar.gz'
RUN su - vscode -c 'tar zxvf ojdbc8-full.tar.gz'
RUN su - vscode -c 'rm ojdbc8-full.tar.gz'
RUN apt install -y graphviz

# schemaspy oracle java8 only support
COPY jre-8u*-linux-x64.tar.gz /home/vscode/
RUN su - vscode -c 'tar zxvf jre-8u*-linux-x64.tar.gz -C /home/vscode --strip-components 1'
RUN su - vscode -c 'rm jre-8u*-linux-x64.tar.gz'
RUN su - vscode -c 'mv /home/vscode/bin/java /home/vscode/bin/java8'
RUN su - vscode -c 'echo export PATH=\$PATH:/home/vscode/bin >> ~/.bashrc'
