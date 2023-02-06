- [Introduction](#introduction)
- [Required-Code-Changes](#required-code-changes)
# Introduction
This document will detail about the aproach we take in phase1 to implement the basic SRE functionalities.
In Phase1 , we wanted to leverage the existing grafana functionalities and write the custom grafana functionalities to implement our features. In phase2 , we will gradually refactor the codebase and will write more independent modules.


please refer to the diagrams below for phase1 and phase2 architecture:
### phase1- architecture

![phase1-architecture](https://raw.githubusercontent.com/AppkubeCloud/appkube-architectures/main/LayeredArchitecture-phase1.svg)

### phase2- architecture

![phase2-architecture](https://raw.githubusercontent.com/AppkubeCloud/appkube-architectures/main/LayeredArchitecture-phase2.svg)


# Phase1 Aproach
Terminology --
**SUI** - Our Stand Alone react based UI
**AWS Cloud Explorer** -- This service will take every AWS account ID as context and will show all the cloud 
elements (WAF / APIGw / CDN / S3 / Route53 / VPC -> EKS/ ECS / EC2 / RDS / Dynamo /.. ) for the account and their element details.

Please refer the design details of AWS explorer as below:

[AWSExplorer](https://www.figma.com/proto/tmzdMgCegtVSQLVgHR6uc3/Netlifi-Usecase-file?page-id=0%3A1&node-id=37%3A16358&viewport=184%2C-681%2C0.04&scaling=scale-down&starting-point-node-id=37%3A16358&show-proto-sidebar=1)  - Shows Cloud ELement Details 

**AWS-API-Server** -- For collecting all the elements data , AWS Cloud Explorer will call the api server.

**Appkube-Catalogue** --  This service will have all the published dashboards / tools etc 
**Appkube-cmdb** -- This service  will have the App / Data services details along with their topology details

# Process Flow
**proposed approach1**
SUI will call the cmdb api's to show every cloud accounts details. The information will be shown as below:
CMDB will have API for all the Data.

![alt](./images/home.jpg)

When a user clicks on any AWS account id , SUI will open up a HTML iframe page 
**iframe**

Link --awsexplorer.synectiks.net?contextId=accId
**iframe**

Inside the iframe the  following screens will open
![alt](./images/CloudElements/cloud-element1.jpg)

![alt](./images/CloudElements/cloud-element2.jpg)

![alt](./images/CloudElements/cloud-element3.jpg)

The above screens will come from awsexplorer where SUI will pass the accounID as context like below:

awsexplorer.synectiks.net?contextId=accId inside iframe.

awsexplorer will be a custom grafana application that has a grafana plugin app of Awsexplorer, that will call the cmdb api's to show logical product and services details and aws-api for element details. 

**proposed approach2**

SUI -> Cloudexplorer (Its a view for every account)
    -> CloudServiceExplorer (its a view inside grafana)
    -> ClusterExplorer (Its a diffrent URL for every cluster)
    -> ClusterServiceExplorer -- It will be a view inside that cluster grafana url)



awsexplorer will maintain views for every account and each of App and Data Services, like as below:

aws-112234344-explorer

![alt](./images/CloudElements/cloud-element2.jpg)

For App and Data Services explorer --

aws-112234344-prod-env-app1-explorer

aws-112234344-prod-env-data1-explorer

![alt](./images/CloudElements/cloud-element4.jpg)

There would be many views that will be retained inside awsexplorer database , say we have HRMS and LOGISTIC prducts and for their PROD env , 

HR-PROD-BusinessService1-Data1  and LOGISTICS-PROD-BusinessService1-Data2, two RDS instance is there.

awsexplorer will maintian two views as follows:

aws-112234344-HR-PROD-BusinessService1-Data1-explorer

aws-112234344-LOGISTICS-PROD-BusinessService1-Data2-explorer

Each of the views will be a composure of few dashboards, say d1/d2/d3/d4.

This dasboards will have variables - say var1.

For RDS / Dynamo , this variables will be the ARN of the databases.

Whenever inside CMDB , we will add any product and its services , proxy API will create this view inside 
awsexplorer database with their variable being associated with the ARN of the RDS/Dynamo etc.

So , 
aws-112234344-HR-PROD-BusinessService1-Data1-explorer ( var1=ARN1)
aws-112234344-LOGISTICS-PROD-BusinessService1-Data2-explorer(var1=ARN2 )

So from SUI , wehn we click enable monitoring for any services , SUI will call a API to awsexplorer 

/createView/ ? Accid=112234344 & PROD=HR & ENV=PROD & ELEMENT=RDS & ARN=arn1

awsexplorer will implement the createView algorithm as follows:

        Get the template view 
        for the AccId , get the right datasource and replace the datasource in the view
        replace the ARN 
        store the new view in database with proper naming convention, and update the view table.

For those cloud elements , where there is no single ARN , say for s3 and lambdas, where for a app and data 
service, multiple S3 bucket or multiple lambdas will be there , SUI , will call createView api as follows

/createViewWithoutArn/ ? Accid=112234344 & PROD=HR & ENV=PROD & ELEMENT=LAMBDA

awsexplorer will implement the createView algorithm as follows:

            Get the template view 
            for the AccId , get the right datasource and replace the datasource in the view
            Set the variable for PROD and ENV
            The query that gets fired to datasource will have prod and env and business service
            store the new view in database with proper naming convention, and update the view table.

            Inside AWS datasource we need to implement this kind of queries where corresponding to product/env / business service , we will get list of s3 buckets or lambda API's.


# Required Code Changes


|API | Description | Input | Output |
|:---|:---|:---|:---|
|/enableMonitoring/{elementId} | enable the monitoring for that cloud element| elementId in CMDB |  return success or failure code|
|Row 2 Column1 | Row 2 Column 2 | Row 2 Column 3 |  Row 1 Column 4 |