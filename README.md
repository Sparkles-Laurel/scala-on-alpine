# scala-on-alpine
An actually decent Scala image based on Alpine that is still huge because of Scala

# why?
- The OpenJDK images were orphaned.
- The `ibmjava` image is huge due to being based on Ubuntu. (see also [the description of the Alpine image comparing it against Ubuntu](https://hub.docker.com/_/alpine))
- There is not an image dedicated for building Scala apps

# how to use
```dockerfile
FROM ghcr.io/sparkles-laurel/scala-on-alpine:0.1.1

RUN apk update && apk upgrade

# Set the working directory
WORKDIR /app

# Copy the project files
COPY . /app

# Run sbt to download dependencies and compile the project
RUN sbt --verbose update && sbt --verbose compile

CMD ["sbt", "run"]
```
