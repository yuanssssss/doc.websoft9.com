---
sidebar_position: 1.4
slug: /app-data
---

# Manage application data

Websoft9 templated application have three data type: 

## Persistent data of containers

Websoft9 use [named volumes](./app-getdetail#volumes) for persisting data generated by application containers.   

That mean if have database container, it also have [database volumes](./app-getdetail#db) of persistent data, you can use [GUI tools for DB](./connectdb).

## External database data

If your application use [external database](./app-getdetail#db), the database data isn't stored on the server.  

## Git repository for deployment

Websoft9 is based GitOps and IaC principles, all deplopment files stored in a [Git repository](./app-compose#configs). 


This approach to data categorization helps Websoft9 to efficiently manage application data while facilitating the separation of configuration and code, simplifying automated deployment and hosted maintenance processes.  