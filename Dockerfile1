FROM openjdk
WORKDIR /app
COPY ./target/my-app-1.0-SNAPSHOT.jar ./
EXPOSE 80
ENTRYPOINT ["java -jar", "my-app-1.0-SNAPSHOT.jar"]