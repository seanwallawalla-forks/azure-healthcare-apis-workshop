# Challenge-01 - Deploy FHIR service (PaaS), FHIR-Proxy (OSS), and FHIR-Bulk Loader (OSS)

## Introduction

Welcome to Challenge-01!

In this challenge, you will use an Azure Resource Manager (ARM) template to deploy **FHIR service** (PaaS), **FHIR-Proxy** (OSS), and **FHIR-Bulk Loader** (OSS). In addition, you will set up a **Postman** environment to make REST API calls to FHIR service.

## Background
FHIR (Fast Healthcare Interoperability Resources) is the standard format for data storage and exchange in Microsoft's health data platform. Microsoft's FHIR infrastructure rests on two Azure components: [FHIR service](https://docs.microsoft.com/en-us/azure/healthcare-apis/fhir/overview) and [Azure API for FHIR](https://docs.microsoft.com/en-us/azure/healthcare-apis/azure-api-for-fhir/overview). For this training, we will be focusing on FHIR service.

In Azure FHIR workflows, FHIR service receives REST API requests from remote client apps and manages all FHIR data persistance and retrieval tasks. Meanwhile, the open-source [FHIR-Proxy](https://github.com/microsoft/fhir-proxy) acts as a checkpoint surrounding FHIR service, filtering the incoming and outgoing FHIR data according to a set of admin-defined rules.

For bulk ingestion of FHIR data into FHIR service, Microsoft offers the open-source [FHIR-Bulk Loader](https://github.com/microsoft/fhir-loader) utility. With FHIR-Bulk Loader, admins can import large amounts of FHIR data with point and click ease. We will be working with FHIR-Bulk Loader in Challenge-03.

## Learning Objectives for Challenge-01
+ Understand the FHIR service - FHIR-Proxy relationship
+ Use an ARM template to deploy FHIR service, FHIR-Proxy, and FHIR-Bulk Loader
+ Configure AAD authentication for FHIR-Proxy and assign app roles
+ Configure Postman for testing FHIR API calls
+ Make FHIR API calls to FHIR service

### FHIR service and FHIR-Proxy Relationship
In the Azure health data platform, FHIR-Proxy acts as a pre- and post-processor, selectively filtering FHIR data on its way into and out of FHIR service. Admins can set up FHIR-Proxy to listen to the stream of I/O data and trigger custom workflows based on specific FHIR events. FHIR-Proxy also brings enhanced Role-Based Access Control (RBAC) to FHIR service, allowing fine-grained authorization for REST API actions at the FHIR Resource level. This also provides a means of Role-Based Consent so that users (i.e., patients) can authorize or deny access to certain FHIR data.

Component View of FHIR-Proxy and FHIR service, with Postman set up to call the FHIR-Proxy endpoint.

<img src="./media/Postman_FHIR-Proxy_API_for_FHIR_ARM_template_deploy.png" height="528">


## Prerequisites 

Before deploying FHIR service, FHIR-Proxy, and FHIR-Bulk Loader, please make sure that you have the following permissions in your Azure environment.

+ **Azure Subscription:** You must have rights to deploy resources at the Resource Group scope in your Azure Subscription (i.e. [Owner](https://docs.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#owner) role).

+ **Azure Active Directory (AAD):** You must have [Application Administrator](https://docs.microsoft.com/en-us/azure/active-directory/roles/permissions-reference#application-administrator) rights for the AAD tenant attached to the Azure Subscription.

You will also need to have [Postman](https://www.getpostman.com/) installed - either the desktop or web client.


## Step 1 - Deploy FHIR service, FHIR-Proxy, and FHIR-Bulk Loader
In the first part of this challenge, you will
- Visit another repo and read the deployment instructions
- Go to the Azure Portal and deploy FHIR service, FHIR-Proxy, and FHIR-Bulk Loader


To begin, **CTRL+click** (Windows or Linux) or **CMD+click** (Mac) on the link below to open the FHIR-Starter quickstarts folder in a new browser tab. 

https://github.com/microsoft/fhir-starter/tree/main/quickstarts 

Follow the instructions and return here when finished.


## Step 2 - Set up Postman and test FHIR service
In the next part of this challenge, you will
- Visit another repo and read the instructions on setting up Postman
- Make API calls to test FHIR service using Postman

To begin, **CTRL+click** (Windows or Linux) or **CMD+click** (Mac) on the link below to open a Postman tutorial in a new browser tab. 

https://github.com/microsoft/health-architectures/tree/main/Postman 

Follow the instructions and return here when finished.

## What does success look like for Challenge-01?
+ FHIR service (PaaS) deployed and available
+ FHIR-Proxy (OSS) deployed and able to communicate with FHIR service
+ FHIR-Bulk Loader (OSS) deployed and available
+ Postman set up and able to connect with FHIR service (directly or via FHIR-Proxy)
    + Capability Statement from the FHIR service server - received
    ```
    {
    "resourceType": "CapabilityStatement",
    "url": "/metadata",
    "version": "1.0.0.0",
    "name": "Microsoft FHIR service 2.2.61 Capability Statement",
    "status": "draft",
    "experimental": true,
    "date": "2022-02-18T00:06:47.9408665+00:00",
    "publisher": "Microsoft",
    ...
    }
    ```
    + `POST AuthorizeGetToken` call in Postman to obtain an AAD access token - succeeded
    + `POST Save Patient` call in Postman to populate FHIR service with a Patient Resource - succeeded
    + `GET List Patients` call in Postman to retrieve a bundle of all Patient Resources stored in FHIR service - succeeded

## Deployed Components 

FHIR service, FHIR-Proxy, and FHIR-Bulk Loader

<img src="./media/Deployed_Components_ARM_template4.png" height="528">

## Next Steps

Click [here](<../Challenge-02 - Convert HL7v2 and C-CDA to FHIR/Readme.md>) to proceed to Challenge-02.