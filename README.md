# conbol program for modern engineer

## prepare

- docker
- vscode

### oracle java
download jre-8u333-linux-x64.tar.gz to .devcontainer/

### vscode extension

install

- ms-azuretools.vscode-docker

## how to launch

Click on the >< symbol in the lower left corner,
.devcontainer launch from vscode 

The oracle database takes time to start up, so please wait 20 minutes.

## compile

```bash
# compile and output executable binary file.
cobc -x src/hello.cob
# compile and output executable binary file(specific output folder).
cobc -x src/hello.cob -o out/bin/hello
# compile and output linux share library.
cobc src/hello.cob -o out/lib/hello.so
```

## 

[oracle cobol](https://docs.oracle.com/en/database/oracle/oracle-database/21/pcbrn/index.html)

## create er figure

```bash
# execute in same folder exits schemaspy.peroperties
java8 -jar /home/vscode/schemaspy.jar
java8 -jar /home/vscode/schemaspy.jar -dbhelp
```

## install sample development data

```bash
enable_sampleschema
```
