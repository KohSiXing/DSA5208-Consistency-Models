# DSA5208-Consistency-Models
This repository contains codes and set up for DSA5208 Assignment 1 - Client Centric Consistency Models

### Software Used
![Python](https://img.shields.io/badge/Python-Programming-blue.svg?style=flat&logo=python&logoColor=FFF)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626.svg?style=flat&logo=Jupyter)
![Docker](https://img.shields.io/badge/Docker-Container-2496ED.svg?style=flat&logo=logo&logoColor=FFF)
![MongoDB](https://img.shields.io/badge/MongoDB-Database-13aa52.svg?style=flat&logo=mongodb&logoColor=FFF)

## Main Scripts

| Script Name                           | Purpose                                                                 |
| ---                                   | ---                                                                     |
| Assignment1.1-combined_cleaned.ipynb  | Conduct experiment under normal conditions                              |
| Assignment1.2-failover_cleaned.ipynb  | Conduct experiment with diconnected secondaries and downed primary node |
| Assignment1.3-partition_cleaned.ipynb | Conduct experiment with network partitions | 

## Previous Work
- Contains the codes and logic on how each of the experiments should be conducted - Consistency Models, Failures and Partition

## Environment Set Up
### To Install Required Python Packages
```
pip install -r requirements.txt
```

### To Set Up C:\Windows\System32\Drivers\etc\Hosts with the following lines:
```
127.0.0.2 mongo1 
127.0.0.3 mongo2
127.0.0.4 mongo3
```

### To Start Docker
```
docker compose up -d
```

### To Initiate Replica Set
```
docker exec -it mongo1 mongosh --eval '
rs.initiate({
  _id: "dsa5208",
  members: [
    { _id: 0, host: "mongo1:27017" },
    { _id: 1, host: "mongo2:27017" },
    { _id: 2, host: "mongo3:27017" }
  ]
});'
```

### To Clean-up the Containers
```
docker compose down -v
```

### MongoDB Compass
```
mongodb://mongo1:27017,mongo2:27017,mongo3:27017/?replicaSet=dsa5208
```
