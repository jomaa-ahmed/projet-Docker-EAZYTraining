# Objectives

The objectives of this practice exam are to ensure that you are able to manage a Docker infrastructure. You will be evaluated on the following themes:

## Themes:
- Improve an existing application deployment process
- Versioning your infrastructure release
- Address best practices when implementing Docker infrastructure
- Infrastructure As Code

## Context

POZOS is an IT company located in France that develops software for High School. The innovation department wants to disrupt the existing infrastructure to ensure that it can be scalable, easily deployed with maximum automation.

POZOS wants you to build a "POC" to demonstrate how Docker can help achieve this goal and showcase its efficiency.

For this POC, POZOS will provide you with an application and wants you to build a decoupled infrastructure based on Docker.

Currently, the application runs on a single server without scalability or high availability. Deploying a new release often results in issues.

In conclusion, POZOS needs agility in its software infrastructure.

## Infrastructure

For this POC, you will use a single machine with Docker installed. The build and deployment will be performed on this machine.

POZOS recommends using CentOS 7.6 OS, as it is widely used within the company. You are authorized to use a virtual machine based on CentOS 7.6, rather than your physical machine.

Security is critical for POZOS DSI, so please do not disable the firewall or other security mechanisms unless justified in your delivery.

## Application

The application you will work on is named "student_list." This basic application enables POZOS to display a list of students with their ages.

**student_list** has two modules:
1. A REST API (with basic authentication) that provides a desired list of students based on a JSON file.
2. A web app written in HTML + PHP that enables end-users to view the list of students.

Your task is to build one container for each module and make them interact with each other.

The source code for the application can be found [here](https://github.com/diranetafen/student-list.git).

### Files to Provide in Your Delivery:
- **docker-compose.yml**: To launch the application (API and web app)
- **Dockerfile**: To build the API image (details provided below)
- **requirements.txt**: Contains all packages needed to run the application
- **student_age.json**: Contains student names with ages in JSON format
- **student_age.py**: Contains the source code of the API in Python
- **index.php**: PHP page where end-users will interact with the service to list students. You need to update `api_ip_or_name` and `port` before running the website container to fit your deployment.
- **docker-compose-registry.yml**: To launch the local registry to save your API

### Explanation of Each File's Role:
- **docker-compose.yml**: Launches the application (API and web app)
- **Dockerfile**: Builds the API image
- **requirements.txt**: Lists packages to be installed
- **student_age.json**: Data source for student ages
- **student_age.py**: API source code in Python
- **index.php**: Web app interface for end-users
- **docker-compose-registry.yml**: Launches a local registry to save your API

## Build and Test (7 points)

POZOS will provide you with information to build the API container.

### API Container Build Instructions:
- **Base Image**: Use `python:3.8-buster`
- **Maintainer**: Specify maintainer information
- **Add Source Code**: Copy API source code to `/` in the container
- **Prerequisites**: Install necessary packages using:
  ```bash
  apt update -y && apt install python-dev python3-dev libsasl2-dev python-dev libldap2-dev libssl-dev -y
