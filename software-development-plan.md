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

## 2. Deliverables
The technical deliverables we anticipate for the project are:
- A web application that allows users to input their symptoms and get a list of possible diseases (frontend)
- A backend system that processes the symptoms and identifies the possible diseases
- Infrastructure as code that allows the repeatable deployment of the web application and the backend system

## 3. Requirements
In this section we describe the requirements we identify for the symptom-solver. Each Requirement will have a unique identifier, which will have the following format: `SYMPREQ-<type>-<number>`. The requirements will be divided into functional and non-functional requirements.

### 3.1. Functional requirements

SYMPREQ-F-001: The system must provide an interactive web frontend where the user can input multiple symptoms that will be used to identify a possible disease the user has. 

SYMPREQ-F-002: Within the interactive web frondend, the system must be able to display static warning messages like a one that advise the user of consulting a healthcare provider for an accurate diagnosis and appropriate treatment. 

SYMPREQ-F-003: Within the interactive web frondend, the system must be able to display dynamic warning messages that result from the backend algorithm processing. 

SYMPREQ-F-004: The interactive web frontend must be responsive and work on all devices. This requirement originates from the need of being able to use the app on a smartphone, tablet, or desktop computer. Additionally, this requirement also originates from risk management, as the app should display all possible diseases and the warning message on all devices and not cut off any information when the screen is too small.

SYMPREQ-F-005: The interactive web frontend must be able to adjust the font sizes of the application according to the screen size. The respective sizes will be chosen acording to DIN 1450 (readability of fonts). This requirement originates from risk management, as the app should display all information in a readable matter, that users can read the information in an ergonomic way and do not have to strain their eyes or hold the device too close to their face and maybe miss some other information.

SYMPREQ-F-006: The interactive web frontend must not allow the user to put the app into fullscreen mode. This requirement originates from risk management, as the app should not be able to hide the operating system or other important warnings or messages from the user.

SYMPREQ-F-007: The symptoms displayed in the interactive web frontend must contain a non-medical language, to be understandable for everyone. This requirement originates from usability engineering, as the usability tests showed that some users do not understand the medical language. There is also a connection to risk management, since understandable symtoms mitigate the risk of misunderstanding.

### 3.2. Non-functional requirements

SYMPREQ-N-001: Maintainability. The app must be designed with modularity and scalability in mind to facilitate easy maintenance and updates to be able to respond to changing conditions, either legal or medical. Small changes, like the addition of a new disease, should, in 95% of the cases, take less than 2 programmer days.

SYMPREQ-N-002: Availability. The symptom-solver app must achieve an uptime of 99.9% per month, excluding scheduled maintenance, equating to no more than 43.2 minutes of unplanned downtime per month. The app must implement disaster recovery and failover mechanisms, to ensure continuous service availability during server failures or critical issues, with a recovery time objective (RTO) of 30 minutes and a recovery point objective (RPO) of 15 minutes. 

SYMPREQ-N-003: Security. The app must encrypt all user data, including personal health information, using AES-256 for data at rest and TLS 1.2 or higher for data in transit. The app must implement multi-factor authentication (MFA) for user login and conduct quarterly security audits and penetration testing, to identify and mitigate at least 95% of high and critical vulnerabilities within 30 days of detection. 

SYMPREQ-N-004: Compatibility. The symptom-solver app must be fully compatible with the latest two major versions of Chrome, Firefox, Safari, and Edge. The website must provide a responsive design that ensures optimal functionality and user experience on both desktop (screen sizes ranging from 1024x768 pixels to 3840x2160 pixels) and mobile devices (screen sizes ranging from 320x568 pixels to 1440x3040 pixels), with consistent performance across various resolutions and orientations. Consistent performance means that the website must load within 3 seconds on both desktop and mobile devices for users with an internet connection speed of at least 5 Mbps, and all interactive elements should respond within 100 milliseconds to user actions.

### 3.3. Boundary conditions:

SYMPREQ-B-001: The data processing must be done in a backend system to ensure, that the algorithms used are not visible to the end users.

## 4. Traceability
The following traceability matrix shows the mapping of requirements to tests. 

| Req / Test    | TC01 | TC02 | TC03 | TC04 | TC05 | TC10 | TC20 |
| ------------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| SYMPREQ-F-001 | X    |      |      |      |      |      |      |
| SYMPREQ-F-002 |      | X    |      |      |      |      |      |
| SYMPREQ-F-003 |      |      | X    |      |      |      |      |
| SYMPREQ-F-004 | X    | X    | X    | X    |      |      |      |
| SYMPREQ-F-005 |      |      |      | X    |      |      |      |
| SYMPREQ-F-006 |      |      |      |      | X    |      |      |
| SYMPREQ-F-007 |      |      |      |      |      |      |      |
| SYMPREQ-N-001 |      |      |      |      |      | X    |      |
| SYMPREQ-N-002 |      |      |      |      |      |      |      |
| SYMPREQ-N-003 |      |      |      |      |      |      |      |
| SYMPREQ-N-004 |      |      |      | X    |      |      |      |
| SYMPREQ-B-001 |      |      |      |      |      |      | X    |

Requirements that are not mapped to a test must be verified manually. This process has to be documented according to the system test specification in the IEC 62304 standard. All tests that can be automated, should be automated.

The following test cases are defined:
- TC01: UI test of the interactive web frontend including the input of symptoms and the display of a possible disease.
- TC02: UI test that checks if the static warning message is displayed.
- TC03: UI test that inputs predefined symptoms that should result in a dynamic warning message.
- TC04: Resposive design UI test that checks predefined screen sizes and if all elements are displayed correctly including symptoms selector, result, and warning messages as well as increasing or decreasing font-sizes. Test screensizes are taken from the compatibility requirement SYMPREQ-N-004.
- TC05: UI test that checks if the app can be put into fullscreen mode. Failure is expected.
- TC10: Architecture test of the backend component using ArchUnit. The test checks whether the backend components are developed using modular and scalable design principles. 
- TC20: Backend test that checks if the data processing is done in the backend system and not in the frontend. Therefore the test calls the backend api with a predefined set of symptoms and checks that the result is processed correctly. Since the frontend is not involved in this test, this test checks the boundary condition SYMPREQ-B-001.

## 5. Configuration management
All components of the systems will have a version number that is incremented with every change. This number must follow the semantic versioning approach that provides version numbers consisting of 3 parts (fix, minor, major). Depending on the scope of the change the semantic version will be increased respectively. All changes will be documented using a changelog that lies in the respective software repository of each component. As the software repository we use GIT. To be able to identify the source code of every version, each final version that is merged into the master branch will be tagged with the semantic version. Additionally for each master merge, a build pipeline will push the resulting artifact into a jfrog artifactory that holds all artifacts in each version of each component. The deployment in the production environment will solely happen with artifacts from the artifactory. Within the build pipeline we run the build tool gradle in a specific version that is fixed within the software repository (gradle.properties). The usage of the gradle wrapper ensures that the correct version will be downloaded for each build. For all external dependencies the version must also be specified in the gradle.properties file. This way each build is deterministic and can be repeated. 

## 6. Safety classification

We classify the software as a class B medical device. The reason is explained below:
All of the diseases listed in the app are non-serious and can be treated at home. The app will not provide any information on serious diseases like cancer, heart attack, stroke, etc. Additionally, the app will not provide any information on mental health conditions. Although there is the case, that our App does not know the disease, in this case, it is very important that the patient seeks further medical advice. The app will advise the user to consult a healthcare provider for an accurate diagnosis and appropriate treatment. In any case, the app displays the static warning message that the user needs to consult a healthcare provider for an accurate diagnosis and appropriate treatment.

## 7. Detailed technical architecture

This section outlines the technical architecture of the Symptomsolver project, ensuring compliance with IEC 62304 and integrating key elements such as system components, data flow, integration, and security mechanisms.

### System Components and Architecture

**Frontend Web Application:**
- **Framework:** Developed using React.js.
- **Functionality:** Enables symptom input and displays diagnoses and warnings.
- **Design:** Responsive and accessible across devices.

**Backend System:**
- **Framework:** Implemented with Node.js and Express.
- **Functionality:** Processes symptoms to identify potential diseases.
- **Data Storage:** Utilizes MongoDB.

  **Backend System - Use of AI:**
- Decision Tree in Python to compute most probable disease based on set of symptoms.
- Training based on publicly available probabilities for diseases => creation of a synthetic dataset. 

**Infrastructure as Code (IaC):**
- **Tools:** Managed with Terraform on AWS for consistent deployments.

### Data Flow and Integration

**Data Flow:**
- **User Input:** Via the frontend.
- **Data Processing:** Backend processes input through RESTful APIs.
- **Diagnosis:** Results displayed on the frontend.

**Integration:**
- **APIs:** RESTful communication between frontend and backend.
- **CI/CD:** Automated with Jenkins for seamless updates.

### Security Mechanisms

**Data Encryption:**
- **At Rest:** AES-256 encryption.
- **In Transit:** TLS 1.2 or higher.

**Authentication:**
- **MFA:** Multi-Factor Authentication.
- **Access Control:** Role-based access.

**Security Audits:**
- **Regular Audits:** Quarterly security audits and penetration tests.

### Documentation and Compliance

**Traceability Matrix:**
- **Requirement Mapping:** Links requirements to tests for compliance verification.

**Configuration Management:**
- **Version Control:** Git with semantic versioning.
- **Artifact Repository:** JFrog Artifactory for version tracking.

**Safety and Risk Management:**
- **Risk Assessment:** Regular assessments with mitigation strategies.
- **Compliance:** Adheres to IEC 62304 standards.

### Connecting to the Software Lifecycle

The detailed technical architecture is integral to the entire software lifecycle, ensuring each phase is interconnected and compliant with IEC 62304:

- **Planning:** The architecture informs the initial planning phase, ensuring all components and interactions are considered from the start.
- **Requirements Analysis:** Architectural components are derived from detailed requirements, ensuring all functional and non-functional needs are met.
- **Design Phases:** The high-level and detailed designs are based on the architecture, ensuring consistent implementation across the project.
- **Implementation and Verification:** Each component is implemented according to the architectural specifications and verified to ensure compliance and functionality.
- **Integration and Testing:** The architecture guides the integration of components, with continuous testing to verify interactions and performance.
- **System Testing:** Overall system tests ensure that the integrated components function as intended within the architectural framework.
- **Software Release:** The final release is based on the fully integrated and tested architecture, ensuring a robust and reliable product.
- **Maintenance:** The architecture provides a foundation for ongoing maintenance and updates, ensuring any changes are systematically integrated and tested.

By embedding the detailed technical architecture within the software lifecycle, Symptomsolver achieves a cohesive and compliant development process, ensuring high standards of quality and performance throughout the project.
