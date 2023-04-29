# 1. DOCKER OVERVIEW
* 

# 2. DIFFERENTS BETWEEN DOCKERFILE INSTRUCTIONS:
* 

# 3. THREE TIER WEB APPLICATION USING DOCKER COMPOSE
## 3.1 Requirements
* Set up a three-tier web application that displays the course attendees’ information on the browser using docker-compose.
* Base image:
    * nginx:1.22.0-alpine
    * python:3.9
    * mongo:5.0

## 3.2 Writting the application code

## 3.3 Configuring Nginx

## 3.4 Writting the Docker Compose file

## 3.5 Writting the Flask and Nginx Dockerfile

## 3.6 Building and running the containers

## 3.7 Import attenddees' information to MongoDB
* Firstly, I will convert the given .xslx file to .json format. The result is given below:
```
{
  "STT": 1,
  "Name": "Bùi Minh Sơn",
  "DOB": 2002,
  "Gender": "Nam",
  "Univerity": "Đại học Công nghệ - Đại học Quốc gia Hà Nội",
  "Major": "Công nghệ thông tin"
 }
 {
  "STT": 2,
  "Name": "Đào Đại Hiệp",
  "DOB": 2001,
  "Gender": "Nam",
  "Univerity": "Đại học Bách khoa Hà Nội",
  "Major": "Điện tử viễn thông"
 }
```


* Then, I copy it to the mongodb container using this command:
'docker cp attendees.json <container id>:/tmp' 

* After that, i will go into the container and import the .json file to a MongoDB database using these commands:
```
docker exec -it mongodb bash
cd tmp
mongoimport --db attendees --collection attendees --file attendees.json
```
    * the -it flag allows me to use the keyboard whem i'm inside the container

## 3.8 Results
* Open the browser and go to http://127.0.0.1:5000/, we can see the results below:
![]()