
**we will be building a simple CI/CD pipeline using Google Cloud Build.**


## Prerequisites: 

To create a CI/CD pipeline: 

- an application code hosted in a Git repository is necessary.
- a simple "Hello, World!" Python file.

## Creating the Build Configuration: 

The core of the pipeline creation involves defining a build configuration file (`cloudbuild.yaml`). This file includes steps, which are the fundamental elements indicating the actions Cloud Build should perform—like building, testing, or deploying the code.

## Defining Steps: 

Each step in the configuration file specifies a particular action. For example, to execute the Python application, opts for the Python image from Docker Hub, ensuring that the appropriate container environment is set up for execution.

> [!NOTE]
> successful code commit and push to the repository will trigger the CI/CD pipeline automatically.


## workflow: 

- create a repository in github.
- create a Personal Access Token in GitHub settings to allow local server to connect with this remote github repo.
- in local server do git clone repo path
- create `main.py` and `cloudbuild.yaml` in local server git repo.
- create a cloud build trigger to trigger a build whenever a push is done from local to remote repo.
- `cloudbuild.yaml` contains command to compile python code and we can add testing and artifacts creation steps. So basically this file contains steps that we want it to perform whenever a change(e.g. push to git remote repo) is made. Hence, continous integration (CI) happens here, it reduces manual toil, errors, long feedfack cycles, built automation.
