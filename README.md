# Webapp

## Architecture Diagram

![diagram](files/diag1.png)

## Aplication Details
Simple API microservice which have nginx as frontend app and passes traffic to flask app which will store name and email to the backend RDS database



## Installation

```bash
➜  ansible-playbook deploy.yml 
```

## Usage
Use curl for accessing the api or UI with the microservice IP


```bash
➜  curl -H "Content-Type: application/json" -d '{"name": "<name>", "email": "<email>" }' http://<Flask service IP>/create -vvv
*   Trying 172.x.x.x:80...
* Connected to 172.x.x.81 (172.x.x.81) port 80 (#0)
> POST /create HTTP/1.1
> Host: 172.x.x.81
> User-Agent: curl/7.71.1-DEV
> Accept: */*
> Content-Type: application/json
> Content-Length: 49
> 
* HTTP 1.0, assume close after body
< HTTP/1.0 200 OK
< Content-Type: application/json
< Content-Length: 29
< Access-Control-Allow-Origin: *
< Server: Werkzeug/2.0.3 Python/3.6.15
< Date: Mon, 15 Jan 2024 13:28:30 GMT
< 
"User created successfully!"
* Closing connection 0
➜  kubernetes-flask-mysql_4 git:(main) ✗```
```
## File Structure

```bash
├── deploy.yml
├── helm_charts
│   └── webapp
│       ├── Chart.yaml
│       ├── charts
│       ├── files
│       │   └── docker
│       │       ├── flaskapi
│       │       │   ├── Dockerfile
│       │       │   ├── flaskapi.py
│       │       │   └── requirements.txt
│       │       └── nginx
│       │           ├── Dockerfile
│       │           └── index.html
│       ├── templates
│       │   ├── flaskapp-deployment.yaml
│       │   ├── flaskapp-service.yaml
│       │   ├── flaskapp_configmap.yaml
│       │   ├── flaskapp_hpa.yaml
│       │   ├── flaskapp_secrets.yaml
│       │   ├── frontend_deployemnt.yaml
│       │   ├── frontend_hpa.yaml
│       │   └── loadbalancer.yaml
│       └── values.yaml
└── roles
    ├── dev
    │   ├── README.md
    │   ├── defaults
    │   │   └── main.yml
    │   ├── files
    │   │   └── values.yaml
    │   ├── handlers
    │   │   └── main.yml
    │   ├── meta
    │   │   └── main.yml
    │   ├── tasks
    │   │   └── main.yml
    │   ├── templates
    │   ├── tests
    │   │   ├── inventory
    │   │   └── test.yml
    │   └── vars
    │       └── main.yml
    ├── production
    │   ├── README.md
    │   ├── defaults
    │   │   └── main.yml
    │   ├── files
    │   │   └── values.yaml
    │   ├── handlers
    │   │   └── main.yml
    │   ├── meta
    │   │   └── main.yml
    │   ├── tasks
    │   │   └── main.yml
    │   ├── templates
    │   ├── tests
    │   │   ├── inventory
    │   │   └── test.yml
    │   └── vars
    │       └── main.yml
    └── staging
        ├── README.md
        ├── defaults
        │   └── main.yml
        ├── files
        │   └── values.yaml
        ├── handlers
        │   └── main.yml
        ├── meta
        │   └── main.yml
        ├── tasks
        │   └── main.yml
        ├── templates
        ├── tests
        │   ├── inventory
        │   └── test.yml
        └── vars
            └── main.yml
```