## Manual Installation
- Install node locally 
- clone repo
- Install dependencies (npm install)
- Setup a Database
    - docker run -e POSTGRES_PASSWORD=PASSWORD@1234 -d -p 5432:5432 postgres
    - get a neontech database
- npx prisma migrate
- npx prisma generate
- npm run build
- npm run start


## Docker Installation
- Install Docker
- Create a network
    - docker network create user_project
- Start postgres
    - docker run --network user_project --name postgres -e POSTGRES_PASSWORD=PASSWORD@1234 -d -p 5432:5432 postgres
- Build docker image 
    - docker build --network=host -t user-project
- Run docker image 
    - docker run -e DATABASE_URL="postgresql://postgres:PASSWORD@1234@postgres:5432/postgres" --network user_project -p 3000:3000 user-project


## Docker-compose Installation
- Install docker, docker-compose
- Run `docker-compose up`
