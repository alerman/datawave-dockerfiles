# DATAWAVE WildFly Docker Image

This image extends `alerman/datawave-base-jdk:8` to copy the wildfly installation from `jboss/wildfly:17.0.1.Final`. The command and work directory are set as they are in the jboss image. **NOTE:** If you wist to be able to use `jmap`, then you must run with `--cap-add=SYS_PTRACE` when launching a container based on this image.


## Building

After updateding the Dockerfile in order to pull the necessary WildFly version and update the labels and other references to the WildFly version, this image is typically built with:
```bash
#Replace VERSION with the version you are building. (e.g. 17.0.1.Final)
docker build -t alerman/datawave-wildfly:VERSION .
```