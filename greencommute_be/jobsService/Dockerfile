FROM  adoptopenjdk/openjdk11
RUN echo $(pwd)
COPY */greencommute_be/jobsService/build/libs/*.jar app.jar
EXPOSE 8081
ENTRYPOINT ["java","-jar","app.jar"]
