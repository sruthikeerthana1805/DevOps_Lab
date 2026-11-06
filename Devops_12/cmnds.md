# EXPERIMENT 12 – SPRING BOOT TESTING, DOCKER AND KUBERNETES



## 2. Test Using Maven

```bash
mvn test
mvn clean test
```

## 3. Build the Spring Boot Application

```bash
mvn clean package
ls target/
```

## 4. Run and Test the Spring Boot Application

```bash
java -jar target/12Exp.jar
```

Open another terminal:

```bash
curl http://localhost:8080/
```

Expected output:

```text
Hello SpringBoot - Experiment 12
```

## 5. Build and Run Docker Container

```bash
docker build -t e12 .
docker run -d -p 8082:8080 --name experiment12-container e12
docker ps
```

## 6. Test Docker Container

```bash
curl http://localhost:8082/
docker logs experiment12-container
```

Expected output:

```text
Hello SpringBoot - Experiment 12
```

## 7. Stop and Remove Docker Container

```bash
docker stop experiment12-container
docker rm experiment12-container
```

## 8. Kubernetes Deployment

Before deployment, open `k8s/deployment.yaml` and set:

```yaml
image: e12
imagePullPolicy: IfNotPresent
```

Apply the deployment and service:

```bash
kubectl get nodes
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

## 9. Check Kubernetes Resources

```bash
kubectl get deployments
kubectl get pods
kubectl get services
```

## 10. Test Kubernetes Application

Run port forwarding:

```bash
kubectl port-forward service/experiment12-service 8083:8080
```

Open another terminal:

```bash
curl http://localhost:8083/
```

Expected output:

```text
Hello SpringBoot - Experiment 12
```

## 11. Delete Kubernetes Resources

```bash
kubectl delete -f k8s/service.yaml
kubectl delete -f k8s/deployment.yaml
```

## 12. Push Project to GitHub (from the Original Laptop)

```bash
git init
git add .
git commit -m "Experiment 12 - Spring Boot Testing Docker Kubernetes"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/12Exp.git
git push -u origin main
```

**Requirements on Linux:**
- Java 21 JDK
- Maven
- Git
- Docker
- A running Kubernetes cluster

**Final Expected Output:**

```text
Hello SpringBoot - Experiment 12
```