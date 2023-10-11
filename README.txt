go get -u github.com/gin-gonic/gin
go get -u github.com/spf13/viper
go get -u github.com/jmoiron/sqlx
go get -u github.com/lib/pq
go get -u github.com/joho/godotenv
go get -u github.com/sirupsen/logrus
go get -u github.com/dgrijalva/jwt-go

go run cmd/main.go
docker run --name=todo-db -e POSTGRES_PASSWORD=1318 -p 5436:5432 -d --rm postgres  

Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
irm get.scoop.sh | iex
// Если не устанавливается scoop
iex "& {$(irm get.scoop.sh)} -RunAsAdmin"
scoop install migrate

migrate create -ext sql -dir ./shema -seq init
migrate -path ./shema -database 'postgres://postgres:1318@localhost:5436/postgres?sslmode=disable' up
migrate -path ./shema -database 'postgres://postgres:1318@localhost:5436/postgres?sslmode=disable' down

// проверка наличия созданных таблиц
docker exec -it 47984fd526f1 //bin//sh
psql -U postgres
\d
exit


// registration
POST:
http://localhost:8000/auth/sign-up/


// authentication
POST:
http://localhost:8000/auth/sign-in/

{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2OTcwMTQ2MzQsImlhdCI6MTY5Njk3MTQzNCwidXNlcl9pZCI6MX0.bKh5kdh0dNTPRjfcMUD_dP-ygJxV7mfMpCn3W6a5JBw"
}


// 
POST:
http://localhost:8000/api/lists/