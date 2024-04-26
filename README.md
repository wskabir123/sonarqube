## SonarQube deployment using docker-compose
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
