EXPERIMENT 12 - SPRING BOOT TESTING, DOCKER AND KUBERNETES

Project folder name: 12Exp
Java package: com.example.exp12
Application port inside the container: 8080

1. Open this folder (12Exp) in VS Code.

2. Run tests:
   mvn test

3. Package the application:
   mvn clean package

   The executable JAR will be created at:
   target/12Exp.jar

4. Build the Docker image:
   docker build -t experiment12-12exp .

5. Run the Docker container:
   docker run -d --name experiment12-container -p 8082:8080 experiment12-12exp

6. Test the Docker application:
   curl http://localhost:8082/

7. Deploy to Kubernetes (make sure the image is available to your Kubernetes
   environment, such as Docker Desktop):
   kubectl apply -f k8s/deployment.yaml
   kubectl apply -f k8s/service.yaml

8. Check Kubernetes:
   kubectl get pods
   kubectl get services

9. Forward the Kubernetes service port:
   kubectl port-forward service/experiment12-service 8082:8080

10. In another terminal:
    curl http://localhost:8082/

Expected response:
Hello SpringBoot - Experiment 12

NOTE:
- This project uses Maven installed on your computer. If you use the Maven
  wrapper from a Spring Initializr project, you can run mvnw.cmd test and
  mvnw.cmd clean package on Windows instead.
- Docker and Kubernetes are optional for running the Spring Boot unit tests.
