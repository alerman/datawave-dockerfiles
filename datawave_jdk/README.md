# DATAWAVE Base JDK Docker Image

This image provides the Azul Zulu OpenJDK version 8u252 and the equivalent functionality from `jboss/base:latest`. The image also installs a number of debugging tools and creates a `datawave` user. **NOTE:** If you wist to be able to use `jmap`, then you must run with `--cap-add=SYS_PTRACE` when launching a container based on this image.

## Building

After updateding the Dockerfile in order to pull the necessary JDK version and update the labels and other references to the Java version, this image is typically built with:
```bash
#Replace VERSION with the version you are building. (e.g. 8u252)
docker build -t alerman/datawave-base-jdk:VERSION .
```

When you update the version, you must also create and pus a version tagged with just the magor jdk version number. For example, if you build `alerman/datawave-base-jdk:8u252`, thne you alo need to tag the new version as `alerman/datawave-base-jdk:8`