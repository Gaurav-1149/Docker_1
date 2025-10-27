## For easy understanding

Here for Docker we were getting an issue that during build stage we were not able to access the postgres container but we needed it to run npx prisma migrate dev
so we did

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


this was very confussing so we did a new thing 
we run the whole script in same order but prisma migrate and run start in the run stage 

build script -> 
 
   "scripts": {
    "build": "tsc -b",
    "start": "node dist/index.js",
    "dev-docker": "npx prisma migrate dev && node dist/index.js"
  },


## new docker script

// Removed host network thing

- Install Docker
- Create a network
    - docker network create user_project
- Start postgres
    - docker run --network user_project --name postgres -e POSTGRES_PASSWORD=PASSWORD1234 -d -p 5432:5432 postgres
- Build docker image 
    - docker build -t user-project .
- Run docker image 
    - docker run -e DATABASE_URL="postgresql://postgres:PASSWORD1234@postgres:5432/postgres" --network user_project -p 3000:3000 user-project
