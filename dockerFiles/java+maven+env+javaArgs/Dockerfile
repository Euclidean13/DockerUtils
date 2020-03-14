FROM docker-image-with-java-and-maven
MAINTAINER Euclidean13

ARG ARCHIVE=**.jar
ARG ARCHIVE_PATH=/**/**/**
ARG LICENSE_PATH=/**/**/**
ENV ENCRYPTPASSWORD=***
COPY ./target/***.jar /home/app/***.jar

# Build a shell script because the ENTRYPOINT command does not like using ENV
WORKDIR /home/app/
RUN echo -e "#/bin/bash\njava -jar -Dhasypt.encryptor.password=\$ENCRYPTPASSWORD -DenvTarget=\$ENVTARGET ./***.jar" > ./entrypoint.sh
RUN chmod +x ./entrypoint.sh
EXPOSE 8080

ENTRYPOINT ["sh", "./entrypoint.sh"]
# For running = docker run -e ENVTARGET=production
