
**we will be building a simple CI/CD pipeline using Google Cloud Build.**


## Prerequisites: 

To create a CI/CD pipeline: 

- an application code hosted in a Git repository is necessary.
- a simple "Hello, World!" Python file.

## Creating the Build Configuration: 

The core of the pipeline creation involves defining a build configuration file (`cloudbuild.yaml`). This file includes steps, which are the fundamental elements indicating the actions Cloud Build should perform—like building, testing, or deploying the code.

## Defining Steps: 

Each step in the configuration file specifies a particular action. For example, to execute the Python application, opts for the Python image from Docker Hub, ensuring that the appropriate container environment is set up for execution.

