# kevinDB
A replicated, fault tolerant, in-memory, key-value database.

## Table of contents
* [Motivation](#motivation)
* [General Info](#general-info)
* [Built-With](#built-with)
* [Server Setup](#server-setup)
* [Storing Data](#storing-data)
* [Contact](#contact)

## Motivation
The motivation for this project was to learn about Docker, REST api's, and maintaining causality among distributed systems by implementing a database 
that stores its data across multiple servers

## General Info
If multiple server instances are running within *kevinDB*:
* Any server that receives a PUT or DELETE operation will delegate that operation to the rest of the running servers. 
* Regardless of communication delays between servers, all servers will perform operations in the same order. 
* Data will persist when servers are created or deleted as long as atleast one server remains running.  

## Built-With
* Docker - 19.03.13
* Node - 12.16.2
* npm - 6.14.4
* python - 3.8.2

## Server Setup
Assuming you everything above installed, to get *kevinDB* up and running with three servers simply run `dockerRun.py` in your terminal. 

## Storing Data
Data can be sent to any running server within kevinDB using an HTTP/1.1 compliant message. Only PUT, GET and DELETE request methods are supported and only strings can be used as keys. A few examples are shown below using [cURL](https://curl.se/). 

Example PUT: to store or update `mykey` with value `secret info`
* `curl --request PUT --header "Content-Type: application/json" --write-out "\n{http_code}\n" --data '{"value": "secret info"}' http://127.0.0.1:8085/key-value-store/mykey`

Example GET: to retrieve item with key `mykey`
* `curl --request GET --header "Content-Type: application/json" --write-out "\n{http_code}\n" http://127.0.0.1:8085/key-value-store/mykey`

Example DELETE: to delete item with key `mykey`
* `curl --request DELETE --header "Content-Type: application/json" --write-out "\n{http_code}\n" http://127.0.0.1:8085/key-value-store/mykey`


## To-do list:
* Support storage for different types of data


## Contact
Created by [@kcharellano](https://www.linkedin.com/in/kcharellano/) - feel free reach out!
