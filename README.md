## How to deploy SonarQube as Docker container and Scan your Project for vulnerability
- Download docker-compose.yaml
- Change admin credentials
- Deploy **docker compose up -d**
- Execute this command if you want to avoid the database error in Postgres
  **docker exec -it $(docker compose ps -q db) psql -U sonartest -d postgres -c "CREATE DATABASE sonar;"**

- After deploying the container download the sonarscan from "https://hub.docker.com/r/sonarsource/sonar-scanner-cli"
- Create a project in your sonarqube and also create a token
- Run the sonar-scan with the ip/hostname of your sonarqube instance and Token for the project:

  **docker run --rm \
  -v "$(pwd):/usr/src" \
  sonarsource/sonar-scanner-cli \
  sonar-scanner \
    -Dsonar.projectKey=sonarscan \
    -Dsonar.sources=. \
    -Dsonar.host.url=http://yoursonarqubeinstance-address \
    -Dsonar.login=Token**

  ![image](https://github.com/wskabir123/sonarqube/assets/59097785/6702e69c-9d63-4766-9f44-aa6e21412a67)

