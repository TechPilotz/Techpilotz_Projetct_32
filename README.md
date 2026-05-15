# Techpilotz_Projetct_32
* Three-Tier Application Deployment using Docker & Docker Compose


This repository demonstrates the deployment of a three-tier application using Docker, focusing on individual Dockerfiles for each component. The application comprises a MySQL database, a Node.js backend, and a React.js frontend.

Prerequisites
Before you begin, ensure that you have the following installed:

Docker
Project Structure
backend: Node.js application serving as the backend.
frontend: React.js application for the frontend.
mysql: Dockerfile and configurations for the MySQL database.
Deployment Steps
MySQL Database:

Navigate to the mysql directory.
Build the MySQL Docker image:
docker build -t mysql-image .
Run the MySQL container:
docker run --name mysql-container --network=three-tier-network -p 3306:3306 -v mysql-data:/var/lib/mysql -d mysql-image
Access the MySQL container:
docker exec -it mysql-container /bin/bash
Inside the container, create tables for the database:
USE school;
CREATE TABLE student (id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(40), roll_number INT, class VARCHAR(16));
CREATE TABLE teacher (id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(40), subject VARCHAR(40), class VARCHAR(16));
Backend Application:

Navigate to the backend directory.
Build the backend Docker image:
docker build -t backend .
Run the backend container:
docker run -d -p 3500:3500 --name backend-container --network=three-tier-network backend
Frontend Application:

Navigate to the frontend directory.
Build the frontend Docker image:
docker build -t frontend .
Run the frontend container:
docker run -d --name frontend-container --network=three-tier-network -p 80:80 frontend
Access the Application:

Open your favorite browser and visit http://localhost:80. Enjoy exploring the MERN stack application!

Data Persistence
Data persistence is ensured by using Docker volumes. If the MySQL container is deleted, data remains available and is automatically added to a new Docker container by providing the same Docker volume.

Feel free to explore and modify the Dockerfiles to enhance your understanding of containerization and deployment! Happy coding! 🚀
