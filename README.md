# Coding Challenge - SamCart

Create two node services to serve details related to cars:

1. To serve as an internal API: GET /cars
2. Service to be used by the API: GET /cars/:id

## Tech Stack Used

1. NodeJS v12.x
2. Docker
3. Express Framework
4. Chai, Mocha, Supertest

## Using this Project

### 1. Running the project directly using Docker Compose

- Go to the root of the project directory
- Run `docker-compose up --build` command

Above command builds and spins two docker containers:

1. `internal-car-service` on port 3000
2. `external-car-service` on port 3001

Now, both services should be accessible using a HTTP client like Postman or Insomnia as follows:

`http://localhost:3000/cars` & `http://localhost:3001/cars`

### 2. Running each service separately

#### 1. Goto service/carsExt and run the following command:

```Bash
$ npm run dev
```

or,

```Bash
$ docker build -t external-car-service .
$ docker -p 3000:3000 -d external-car-service
```

#### 2. Goto service/carsInt and run the following command:

```Bash
$ npm run dev
```

or,

```Bash
$ docker build -t internal-car-service .
$ docker -p 3000:3000 -d internal-car-service
```

## Sanity Check

(1) Internal Car Service

| Endpoint  | HTTP Method | Result                |
| --------- | ----------- | --------------------- |
| /         | GET         | server is up          |
| /cars     | GET         | list of all the cars  |
| /cars/:id | GET         | car with specified id |

(2) External Car Service

| Endpoint      | HTTP Method | Result                |
| ------------- | ----------- | --------------------- |
| /             | GET         | server is up          |
| /cars         | GET         | list of all the cars  |
| /cars?id=abcd | GET         | car with specified id |

## Running the Unit tests

Make sure that both the services are running as separate containers. This can be achieved using following command:

```Bash
$ docker-compose up --build
```

### (1) Unit Tests for Internal Cars Service

(1) Goto `services/carsInt
(2) Make sure that all the node dependecies are installed locally:

```Bash
$ npm install
```

(3) Run the following coommand:

```Bash
$ npm test
```

### (1) Unit Tests for External Cars Service

(1) Goto `services/carsEnt
(2) Make sure that all the node dependecies are installed locally:

```Bash
$ npm install
```

(3) Run the following coommand:

```Bash
$ npm test
```
