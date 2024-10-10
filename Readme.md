# Simple Java Application CI/CD Pipeline

This repository contains a Jenkins pipeline for a simple Java application. The pipeline automates the build, test, and deployment processes using Maven and Docker.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Pipeline Overview](#pipeline-overview)
- [Setup Instructions](#setup-instructions)
- [Usage](#usage)
- [License](#license)

## Prerequisites

Before you begin, ensure you have the following installed:

- **Jenkins**: An instance of Jenkins running with the necessary plugins installed.
- **Maven**: The Maven tool should be configured in Jenkins.
- **Docker**: Docker must be installed on the target machine where the application will be deployed.
- **SSH Access**: Ensure SSH access is configured for the Jenkins server to communicate with the remote server.

## Pipeline Overview

The pipeline consists of the following stages:

1. **Start CI & Git Checkout**: Initializes the CI process and checks out the code from the Git repository.
2. **Maven Install**: Cleans, tests, and packages the Java application using Maven.
3. **Publish Over SSH**: Transfers the packaged WAR file and Dockerfile to the remote server and deploys the application using Docker.
4. **End CI**: Marks the end of the CI process.

## Setup Instructions

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/nbhovare/simple-app-java.git
   cd simple-app-java
