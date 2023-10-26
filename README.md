# Creative Solutions User API
This repository serves a user api through the use of a local kind kubernetes cluster

You need to install  `WSL` `docker-deskstop`  and `helm` binaries manually to deploy the api in a local kubernetes cluster.


# API
- CreateUser
- Get Single User by Email
- Get all users
- Load User in json data

# Technologies
- Nodejs
- Express
- Mongodb
- Kubernetes
- Helm


# Running the API
## Requirements and Installation

To install and run this project you would need to have Node.js installed.

- Create a .env file in the root directory of the cloned project and add the following:
  - MONGO_URI=<mongouri>
  - ROUNDS=<Number of rounds to hash password>
  - NODE_ENV=<nodeenvironment>

- To run:

```sh
cd api
npm install
npm run start
```

## Testing

```sh
npm run test
```

## API-ENDPOINTS

   ## USERS
   
`- POST /api/createUser Create user account`

```json
{
	"first_name": "obaweya",
	"last_name": "dayo",
	"email": "sesan@yahoo.com",
	"password": "randompassword"
}
```

`- POST /api/singleUser Get a single User`

```json
{
	"email":"admin@gmail.com"
}
```

`- GET /api/ Get all Users`

`- GET /api/health Get a single User`


# Deployment
### 1. Docker Compose
```sh
docker-compose up -d
```
This exposes the api on (http://localhost:8080/api/health)[http://localhost:8080/api/health]


### 2. image Push to docker Hub

```sh
docker tag `image-name` `hubusername/localname`
```
```sh
docker push  `hubusername/localname:v1`
```

### 3. helm chart create

```sh
helm create `chart-name`
```

### 4. helm test
```sh
helm install `realease-name` --debug --dry-run `chart-name`
```


### 5. helm install

```sh
helm install `realease-name` `chart-name`
```


## 6. verify
```sh
helm list -A
kubectl get deployment 
kubectl get svc
```
<img src="images/Screenshot 2023-10-26 190057.png" alt="Alt text">

View the application using:
`https://localhost/api/health`

<img src="images/Screenshot 2023-10-26 190149.png" alt="Alt text">

- CI/CD can be added using a couple of options. i did not go into that as the focus was only on local deployment
