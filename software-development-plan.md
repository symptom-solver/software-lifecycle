# Software Development Plan of the sympom-solver project
This document describes the software development plan of the sympom-solver project. The project is a web application that helps users to identify the possible diseases based on the symptoms they have. 

## 1. Development models
The project will be developed using the scrum development model. The scrum model is chosen because it is an agile development model that allows the team to deliver the product incrementally. The project will be divided into sprints, each sprint will last for two weeks. At the end of each sprint, the team will deliver a working product increment that will be presented in a sprint review to the stakeholders. The team will have a sprint planning meeting at the beginning of each sprint to plan the work for the sprint as well as a daily standup meeting to discuss the progress and any issues. 
Because the project is a medical device, all the development activities will be conducted in compliance with the IEC 62304 standard. The standard defines the software development process for medical devices and provides guidance on how to develop software that is safe and effective. The process described by the standard contains the phases Planning, Architecture, Detailed Design, Implementation and Verification, Integration and Testing, System Testing and Software Release. These are mapped to the scrum development model but not all be done at each level. The mapping is as follows:
- Each sprint all phases will be done, except for the Release, since each sprint is carried out like a small project
- The release phase will be done once per release
- All other levels, like the increment or the bigger release or the even bigger product contain the planning phase
- Tests will be done once per increment and per release
- The architecture and requirements phases will be done for the whole product. These are the only phases that are done in addition to every single sprint. 

Our team chose the scrum model because we expect to have changes throughout the long running project and the scrum model is well suited for projects with changing requirements because of its iterative approach. 

## 2. Devliverables

TODO

## 3. Requirements
In this section we describe the requirements we identify for the symptom-solver. Each Requirement will have a unique identifier, which will have the following format: `SYMPREQ-<type>-<number>`. The requirements will be divided into functional and non-functional requirements.

### 3.1. Functional requirements

SYMPREQ-F-001: The system must provide an interactive web frontend where the user can input multiple symptoms that will be used to identify a possible disease the user has. 
SYMPREQ-F-002: Within the interactive web frondend, the system must be able to display static warning messages like a one that advise the user of consulting a healthcare provider for an accurate diagnosis and appropriate treatment. 
SYMPREQ-F-003: Within the interactive web frondend, the system must be able to display dynamic warning messages that result from the backend algorithm processing. 

TODO: further requirements and the connection to usability and risk management

### 3.2. Non-functional requirements

SYMPREQ-N-001: 

TODO: further requirements and the connection to usability and risk management


### 3.3. Boundary conditions:

SYMPREQ-B-001: The data processing must be done in a backend system to ensure, that the algorithms used are not visible to the end users.

TODO: further requirements and the connection to usability and risk management


## 4. Traceability
How do you show that each requirement was implemented and tested?

TODO: Traceability matrix, using: https://www.tablesgenerator.com/markdown_tables

## 5. Configuration management
All components of the systems will have a version number that is incremented with every change. This number must follow the semantic versioning approach that provides version numbers consisting of 3 parts (fix, minor, major). Depending on the scope of the change the semantiv version will be increases respectively. All changes will be documented using a changelog that lies in the respective software repository of each component. As the software repository we use GIT. To be able to identify the source code of every version, each final version that is merged into the master branch will be tagged with the semantic version. Additionally for each master merge, a build pipeline will push the resulting artifact into a jfrog artifactory that holds all artifacts in each version of each component. The deployment in the production environment will solely happen with artifacts from the artifactory. Within the build pipeline we run the build tool gradle in a specific version that is fixed within the software repository (gradle.properties). The usage of the gradle wrapper ensures that the correct version will be downloaded for each build. For all external dependencies the version must also be specified in the gradle.properties file. This way each build is deterministic and can be repeated. 

## 6. Safety classification

TODO