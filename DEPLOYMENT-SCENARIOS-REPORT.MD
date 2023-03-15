# IDS Testbed and deployments report

## 1. Introduction

#### 1.1 What is a Data Space? 
According to the definition by IDSA, a data space is a secure and standardized digital infrastructure that enables trusted data exchange and data-based services among various stakeholders. In the IDS definition, a data space is a virtual space that provides a standardized framework for data exchange, based on common protocols and formats, as well as secure and trusted data sharing mechanisms. The IDS data space is designed to support data sovereignty, meaning that data owners retain control over their data and can determine who has access to it and under what conditions.

The IDS data space is intended to support a wide range of applications and industries. The data space is designed to be interoperable with other data spaces, enabling seamless data exchange across different domains and industries. Overall, the IDS data space is a flexible and scalable domain and technology-agnostic framework that enables secure and trusted data exchange and services, while preserving data sovereignty and privacy.

#### 1.2 What are cool use cases and why do we need data spaces?
The International Data Spaces standard enables cross-company business processes known as use cases. These use cases play a crucial role in identifying, analyzing, and evaluating user requirements for IDS. Moreover, by implementing a use case, companies can foster innovation and create an ecosystem by involving internal and external stakeholders in the development of smart value-added services. Use cases serve as the fuel for data spaces, which act as the engine. They facilitate and expedite the creation of cross-domain and cross-country data spaces with numerous participants.
[Data Spaces Overview](https://internationaldataspaces.org/wp-content/uploads/dlm_uploads/Data_Spaces_Radar_Web_230307.pdf) brochure that is available via [Most Important Documents](https://internationaldataspaces.org/publications/most-important-documents/) page of IDSA Website lists the use cases along with the challenges they are tackling, the success stories behind and the components used in each scenario to enable data sharing in a secure and sovereign way. This document gets updated on an annual basis.

#### 1.3 Technically speaking, what is a data space?
![Data Sharing in a Data Space](/images/IDSA-Infographic-Data-Sharing-in-a-Data-Space.jpg)

#### 1.4 Connectors
Connector report
Graduation Scheme table

#### 1.5 MVDS, what are the services we need?

## 2. Foundation - Terms and Definitions
[IDS Glossary](https://github.com/International-Data-Spaces-Association/IDS-G/tree/main/Glossary) acts as the ultimate source of truth for terms and definitions. 
* there are different things to be known before
* what do you want to do
  * Testing for validation
  * testing for playing around
  * testing for extension
  * providing services

### 2.1 IDS Testbed
[IDS Testbed](https://github.com/International-Data-Spaces-Association/IDS-testbed) is an invaluable tool for ensuring that components conform to the IDS specifications for connection and communication. It is a setup that utilizes Open Source IDS components and enables organizations to verify that their own components work interoperably with other IDS components within the testbed. The testbed provides organizations with the ability to conduct component behavior testing and interoperability testing against various IDS components (such as the Connector, DAPS, CA, and Metadata Broker).

Moreover, the IDS Testbed is also a great place to start preparing for IDS certification. By utilizing the testbed, organizations can thoroughly test their components and ensure that they meet the necessary requirements for IDS certification. The testbed can help organizations identify any issues with their components before they are certified, thereby minimizing any potential disruptions during the certification process.

In addition to testing and certification, the IDS Testbed can also serve as a starting point for creating data spaces. The testbed provides a framework for organizations to begin building their own data spaces with confidence. By ensuring interoperability and compatibility between various components, organizations can have a solid foundation upon which to build their data spaces. The IDS Testbed is a powerful tool that enables organizations to develop, test, and certify components and data spaces that adhere to the IDS specifications and work seamlessly with other IDS components.

### 2.2 IDS Deployment Scenarios
An IDS deployment scenario is a description of the steps and processes involved in delivering a component or a set of components to end-users. It outlines the various stages of deployment, from development and testing to release and optionally maintenance. The scenario typically includes information on the prerequisites (such as hardware and software requirements), configuration settings, and any necessary third-party integrations. It also includes details on the deployment environment, such as whether it will be installed on-premises or in the cloud, and how the system will be monitored and supported once it is live. A deployment scenario helps ensure that the deployment process is consistent, easily repeatable, reusable and efficient, and that the system is deployed in a way that meets the needs of end-users.

In an IDS Deployment Scenario, the definition of purpose (or the problem challenged/solved) is crucial. For example: 
Implementor A implements a data space (consisting of open-source components) that allows secure and sovereign data sharing between educational institutions (high schools, professional training centres, universities) and relevant public bodies (employment agencies and municipalities). Let's assume that this data space provides data exchange between these parties, so that the public bodies can reduce the number of potentially unemployed people, to fight unemployment in the country. 

Then Implementor B comes and takes this implementation, makes small modifications to tailor it to the needs of the tourism industry. In their case, the data space enables secure and sovereign data sharing between the hotels in tourism industry and public bodies. In this example, hotels provide various data sets (such as number of rooms booked, the average length of stay, the average room rate) with public bodies. Public bodies can use this data to analyze visitor demographics and travel patterns which allows them to make better decisions about tourism policies, investments, and promotions. 

This is a good example of two IDS Deployment Scenarios. Even if both setups consist of very similar components, the difference in purpose and area of use makes them two different deployment scenarios.

* differentiate between
  * complex technologic additions
  * "just" usage of technologies, like a connector being used by an organization in projects, for various purposes
  
#### 2.2.1 How to join to Deployment Scenarios? call to action
Why should one share a deployment scenario? 
Because we are in the early steps of the technology. 

What advantages does it provide? More visibility, your experiment will be exposed to more people. Potential contributors.

### 2.3 Testbeds
* list and describe the testbeds

## 3. IDS Assets & Relationships
brief introduction, how to read this section
* Relationship of IDSA Assets: How one can use them and at what stage of development? (End User Perspective)
* Relationship of IDSA Assets: How do they interact with each other? (IDSA Perspective)
* include cool figures from Anil and Christoph

**City Analogy**
The city analogy is a powerful and effective way to understand the concept, structure, functionality and role of data spaces. While highlighting the similarities between data spaces and physical cities, one can not only understand the key features and functions of data spaces in an easier way, but also can better understand how this technology will evolve in the future.

Just as cities consist of many elements and zones such as residential areas, industrial zones and commercial zones, data spaces consist of components that fulfill the roles to enable secure and sovereign data exchange between parties. Like cities, data spaces are made up of different neighborhoods or domains, each with its own unique character and needs. For example, a manufacturing data space may have different requirements than a healthcare data space, and each domain may have its own data owners, data consumers, and service providers.

Within each data space, there are rules and regulations that govern how data is accessed, used, and shared. Just as cities have laws and regulations that ensure the safety and well-being of their residents, data spaces have policies and protocols that ensure the security and privacy of data. These policies and protocols may vary across different data spaces and domains, depending on the needs and preferences of their stakeholders.

Data spaces also have gateways or portals that connect them to other data spaces and domains, just as cities have transportation networks that connect them to other cities and regions. These gateways enable seamless data exchange and collaboration across different domains and industries, and enable stakeholders to leverage the strengths and resources of other data spaces.

In addition to gateways, data spaces may also have marketplaces or platforms where stakeholders can buy, sell, or exchange data-based services, just as cities have markets and commercial districts where people can buy, sell, or trade goods and services.

Like cities, data spaces are constantly evolving and adapting to changing needs and conditions. As new technologies and data sources emerge, data spaces may need to update their infrastructure, policies, and protocols to ensure that they remain relevant and effective.

Just as cities are shaped by the people who live and work in them, data spaces are shaped by their stakeholders. The success of a data space depends on the willingness of its stakeholders to share and collaborate, and to create a vibrant and dynamic digital ecosystem that benefits everyone.

## Outlook and next steps
