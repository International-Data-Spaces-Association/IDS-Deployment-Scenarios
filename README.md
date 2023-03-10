# IDS Deployment Scenarios
This repository lists IDS Deployment Scenarios from various domains and cases. It serves as a library of information, listing different deployment alternatives applied by IDS projects. The ultimate aim is to create a source of inspiration and guidance for those who wish to experiment with data spaces or search for the best deployment practices. This repository also serves as a platform where everyone can express their opinions on the existing deployment scenarios by creating issues and initiating discussions around them.

## List of Existing IDS Deployment Scenarios

| Name of the Deployment Scenario | Provider | Description | Used Components | 
| -------- | -------- | -------- | -------- |
| [Minimum Viable Data Space](Deployment-Scenarios/minimum-viable-data-space-top-ix.md) | [TOP-IX](https://www.top-ix.org/it/home/) | An example deployment of Minimum Viable Data Space (as defined by IDSA) | CA, DAPS and Connector |
| [IDS Testbed Deployment Using Kubernetes Architecture](Deployment-Scenarios/minimum-viable-data-space-using-k8s.md) | [ATOS](https://atos.net/es/spain) | How to deploy an IDS-Testbed using Kubernetes | CA, DAPS and Connector |

:rocket: [Minimum Viable Data Space](https://github.com/International-Data-Spaces-Association/IDS-testbed/blob/master/minimum-viable-data-space/MVDS.md) is also included as a deployment scenario, defined by IDSA Head Office. It is also a great place to start creating a deployment scenario.

## What is an IDS Deployment Scenario? 
An IDS deployment scenario is a description of the steps and processes involved in delivering a component or a set of components to end-users. It outlines the various stages of deployment, from development and testing to release and optionally maintenance. The scenario typically includes information on the prerequisites (such as hardware and software requirements), configuration settings, and any necessary third-party integrations. It also includes details on the deployment environment, such as whether it will be installed on-premises or in the cloud, and how the system will be monitored and supported once it is live. A deployment scenario helps ensure that the deployment process is consistent, easily repeatable, reusable and efficient, and that the system is deployed in a way that meets the needs of end-users. 

A deployment scenario can be considered as any implementation made with IDS-compliant components:
- that allows sovereign data sharing (as defined by IDSA)
- is built with a clear purpose, to solve a problem
- is adequately documented to enable others to follow the same path

### Example: 
![](images/IDS-Deployment-Scenarios-Patterns.png)
As depicted on the image above, there are several ways to create a deployment scenario. As long as the implementation is made for a purpose and contains an IDS-compliant component, it can be considered as an IDS Deployment Scenario. 

An envisaged flow for running an experiment with a IDS Deployment Scenario can be considered as depicted on the image below:
![](images/creationprocess.png)

### Why Should I Share My Deployment Scenario with Others?  
Sharing your deployment scenario with others is an essential part of the open source philosophy, which is based on the idea that collaboration and sharing knowledge leads to better results. By sharing your deployment scenario, you allow others to learn from your experience and benefit from your insights, potentially saving them time and effort in their own deployment process.

Sharing deployment scenarios with others can also have many advantages for the original implementor, including:

- **Getting recognized**: Sharing deployment scenarios with others can help the original implementor get recognized for their work. By sharing their scenarios, they can showcase their expertise and demonstrate their ability to solve complex problems.

- **Feedback and improvement**: When others use the deployment scenarios, they may provide feedback and suggest improvements. This can help the original implementor refine their work and make it even better.

- **Collaboration**: Sharing deployment scenarios with others can foster collaboration and create a community of people who are interested in similar topics. This can lead to new partnerships, joint projects, and opportunities to learn from others.

- **Feel good factor**: Sharing deployment scenarios with others can give the original implementor a sense of satisfaction and fulfillment. Knowing that their work is helping others and making a positive impact can be very rewarding.

### Relationship with Data Space Radar
Level 3 (Pilot) and Level 4 (Live) are considered to be candidates for IDS Deployment Scenarios.


### How to assess the maturity level of a IDS Deployment Scenario?


## How can I share a deployment scenario?
You are warmly invited to contribute to the IDS Deployment Scenarios in two ways: 

Send a pull request 
Or if you are already on your way to share a use case (via Data Space Radar) you can also do that. 

:triangular_flag_on_post: Either by suggesting to list a deployment scenario here by using [the Data Space Radar form](https://forms.office.com/Pages/ResponsePage.aspx?id=NNZGs_usx0K9RPFVfuibG3WVHeFvj2hHgjU7ZCgshUhUMExMOTdCWDNMSERJTjlIUlRKMVc0QTUxMCQlQCN0PWcu). 

:bulb: Or by expressing your idea, suggest something new (or asking a question) on a specific deployment scenario by creating an issue, by checking the contribution rules on [CONTRIBUTING.md](CONTRIBUTING.md), and the [Code of Conduct](CODE_OF_CONDUCT.md).

## Is there a template I should follow? 
No, not yet.
We recommend that your deployment scenario to contain: 
- Prerequisites 
- System Requirements: Specify the minimum hardware and software requirements necessary for the successful deployment of the system.
- If any network configuration is required
- Deployment diagram (to show which environment each component is deployed) Docker, Kubernetes Server, etc. Describe the overall architecture of the system, including any third-party components or integrations.
- Which components are used in the scenario 
- What purpose the entire deployment is made for? What problem does it try to solve? Clearly define the purpose of the deployment scenario, including the intended use case and expected outcomes.
- Deployment Process: Describe the deployment process, including any installation, configuration, or testing procedures.
- Any other resources that might be helpful to reproduce the scenario.


