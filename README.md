# GoMigrate

## Start db
docker run --name postgres -d -p 5432:5432 --env POSTGRES_USER=postgres --env POSTGRES_PASSWORD=password --env POSTGRES_DB=example postgres:13-alpine

## Set db url
export DB_URL='postgres://postgres:password@localhost:5432/example?sslmode=disable'

## Create tables
migrate -database ${DB_URL} -path db/migrations up

## Generate data models
jet -dsn=${DB_URL} -schema=public -path=./db/models