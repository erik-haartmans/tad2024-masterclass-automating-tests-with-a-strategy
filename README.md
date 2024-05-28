# TAD2024 - Masterclass: Automating tests with a strategy

This readme contains the slides & steps for the masterclass which will be presented.

You will find the information needed to follow the steps for the journey into "shifting tests left".

![alt text](images/image.png)

![alt text](images/image-1.png)

![alt text](images/image-2.png)

![alt text](images/image-3.png)

![alt text](images/image-4.png)

# Meet the System Under Test (SUT)

![alt text](images/image-5.png)

![alt text](images/image-6.png)

![alt text](images/image-7.png)

## https://tas.frontend.staging.polteq-testing.com

![alt text](images/image-8.png)

## https://github.com/erik-haartmans/tas-e2e-testing-repo-java

![alt text](images/image-9.png)

![alt text](images/image-10.png)

![alt text](images/image-11.png)

![alt text](images/image-12.png)

![alt text](images/image-13.png)

![alt text](images/image-14.png)

![alt text](images/image-15.png)

![alt text](images/image-16.png)

![alt text](images/image-17.png)

![alt text](images/image-18.png)

![alt text](images/image-19.png)

# Bug alert ...

![alt text](images/image-20.png)

![alt text](images/image-21.png)

![alt text](images/image-22.png)

![alt text](images/image-23.png)

# Can we test more efficiently?

![alt text](images/image-24.png)

![alt text](images/image-25.png)

![alt text](images/image-26.png)

![alt text](images/image-27.png)

![alt text](images/image-28.png)


# Description of the endpoints
## tas-bff-service endpoint: /register-user
```
  - path: /register-user
    method: POST
    request:
      body:
        application/json:
          schema: |
              {
                "name": "Max Verstappen",
                "email": "m.verstappen@redbullracing.com",
                "password": "password123",
                "phoneNumber": "555-12345"
              }
    responses:
      - status: 200
        body:
          application/json:
            schema: |
              {
                "name": "Max Verstappen",
                "email": "m.verstappen@redbullracing.com",
                "password": "password123",
                "phoneNumber": "555-12345"
              }
      - status: 400
        body:
          application/json:
            schema: |
              {
                "statusCode": 400,
                "message": "Name is required, Email is required"
              }
```

## tas-bff-service endpoint: /login
```
  - path: /login
    method: POST
    request:
      body:
        application/json:
          schema: |
              {
                "email": "m.verstappen@redbullracing.com",
                "password": "password123",
              }
    responses:
      - status: 200
        body:
          application/json:
            schema: |
              {
                "name": "Max Verstappen",
                "email": "m.verstappen@redbullracing.com",
                "phoneNumber": "555-12345"
              }
      - status: 403
        body:
          application/json:
            schema: |
              {
                "statusCode": 403,
                "message": "Could not login with these credentials"
              }
```
# API Testing

![alt text](images/image-29.png)

![alt text](images/image-30.png)

![alt text](images/image-31.png)

![alt text](images/image-32.png)

![alt text](images/image-33.png)

![alt text](images/image-34.png)

![alt text](images/image-35.png)

# The SUT in even more detail

![alt text](images/image-36.png)

![alt text](images/image-37.png)

![alt text](images/image-38.png)

# Component Testing: tas-user-service

![alt text](images/image-39.png)

![alt text](images/image-40.png)

![alt text](images/image-41.png)

![alt text](images/image-42.png)

![alt text](images/image-43.png)

# tas-user-service endpoint: /user
```
  - path: /user
    method: POST
    description: create a user
    request:
      body:
        application/json:
          schema: |
              {
                "name": "Max Verstappen",
                "email": "m.verstappen@redbullracing.com",
                "password": "password123",
                "phoneNumber": "555-12345"
              }
    responses:
      - status: 200
        body:
          application/json:
            schema: |
              {
                "name": "Max Verstappen",
                "email": "m.verstappen@redbullracing.com",
                "password": "password123",
                "phoneNumber": "555-12345"
              }
      - status: 400
        body:
          application/json:
            schema: |
              {
                "statusCode": 400,
                "message": "Name is required, Email is required"
              }
```

![alt text](images/image-44.png)

![alt text](images/image-45.png)

![alt text](images/image-46.png)

![alt text](images/image-47.png)

![alt text](images/image-48.png)

# https://github.com/erik-haartmans/tas-user-service

![alt text](images/image-49.png)

![alt text](images/image-50.png)

![alt text](images/image-51.png)

![alt text](images/image-52.png)

![alt text](images/image-53.png)

![alt text](images/image-54.png)

![alt text](images/image-55.png)

![alt text](images/image-56.png)

![alt text](images/image-57.png)

![alt text](images/image-58.png)

![alt text](images/image-59.png)

![alt text](images/image-60.png)

![alt text](images/image-61.png)

![alt text](images/image-62.png)

# Component Test: `tas-frontend`

![alt text](images/image-63.png)

![alt text](images/image-64.png)

![alt text](images/image-65.png)

![alt text](images/image-66.png)

## tas-bff-service: /register-user
```
  - path: /register-user
    method: POST
    request:
      body:
        application/json:
          schema: |
              {
                "name": "Max Verstappen",
                "email": "ver@redbullracing.com",
                "password": "password123",
                "phoneNumber": "555-12345"
              }
    responses:
      - status: 200
        body:
          application/json:
            schema: |
              {
                "name": "Max Verstappen",
                "email": "ver@redbullracing.com",
                "password": "password123",
                "phoneNumber": "555-12345"
              }
      - status: 400
        body:
          application/json:
            schema: |
              {
                "statusCode": 400,
                "message": "Name is required, Email is required"
              }
```

## tas-bff-service: /login
```
  - path: /login
    method: POST
    request:
      body:
        application/json:
          schema: |
              {
                "email": "ver@redbullracing.com",
                "password": "password123"
              }
    responses:
      - status: 200
        body:
          application/json:
            schema: |
              {
                "name": "Max Verstappen",
                "email": "ver@redbullracing.com",
                "phoneNumber": "555-12345"
              }
      - status: 403
        body:
          application/json:
            schema: |
              {
                "statusCode": 403,
                "message": "This can be any message"
              }
```

![alt text](images/image-68.png)

![alt text](images/image-69.png)

![alt text](images/image-70.png)

# https://github.com/erik-haartmans/tas-frontend

![alt text](images/image-71.png)

![alt text](images/image-72.png)

![alt text](images/image-73.png)

![alt text](images/image-74.png)

![alt text](images/image-75.png)

![alt text](images/image-76.png)

![alt text](images/image-77.png)

![alt text](images/image-78.png)

# Component Test: `tas-login-service` using WireMock

![alt text](images/image-79.png)

![alt text](images/image-80.png)

![alt text](images/image-81.png)

![alt text](images/image-82.png)

## tas-login-service: api spec /login endpoint
```
  - path: /login
    method: POST
    request:
      body:
        application/json:
          schema: |
              {
                "email": "ver@redbullracing.com",
                "password": "password123"
              }
    responses:
      - status: 200
        body:
          application/json:
            schema: |
              {
                "name": "Max Verstappen",
                "email": "ver@redbullracing.com",
                "phoneNumber": "555-12345"
              }
      - status: 403
        body:
          application/json:
            schema: |
              {
                "statusCode": 403,
                "message": "Could not login with these credentials"
              }
```

## tas-user-service: api spec /users/{email} endpoint
```
  - path: /users/{email}
    method: GET
    responses:
      - status: 200
        body:
          application/json:
            schema: |
              {
                "name": "Max Verstappen",
                "email": "ver@redbullracing.com",
                "password": "1234"
                "phoneNumber": "555-12345"
              }
      - status: 404
        body:
          application/json:
            schema: |
              {
                "statusCode": 404,
                "message": "Could not find user bla@bla.com"
              }
```

![alt text](images/image-83.png)

![alt text](images/image-84.png)

## Mocked response tas-user-service: user found
```json
{
  "request": {
    "method": "GET",
    "url": "/users/a@a.nl"
  },
  "response": {
    "status": 200,
    "headers": {
      "Content-Type": "application/json"
    },
    "jsonBody": {
      "name": "fake user a",
      "email": "a@a.nl",
      "password": "password",
      "phoneNumber": "0612345678"
    }
  }
}
```

## Mocked response tas-user-service: user not found
```json
{
  "request": {
    "method": "GET",
    "url": "/users/not@successful.login"
  },
  "response": {
    "status": 404,
    "headers": {
      "Content-Type": "application/json"
    },
    "jsonBody": {
      "statusCode": 404,
      "message": "Could not find user not@successful.login"
    }
  }
}
```

![alt text](images/image-85.png)

![alt text](images/image-86.png)

![alt text](images/image-87.png)

# RECAP

![alt text](images/image-88.png)

![alt text](images/image-89.png)

![alt text](images/image-90.png)

![alt text](images/image-91.png)

![alt text](images/image-92.png)

![alt text](images/image-93.png)

![alt text](images/image-95.png)

![alt text](images/image-96.png)