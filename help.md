##Execute this command if you want to avoid the database error in Postgres
docker exec -it $(docker compose ps -q db) psql -U sonartest -d postgres -c "CREATE DATABASE sonar;"
