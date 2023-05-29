## Organization
| method | end point | Request | Response | Description | 
|:---|:---|:---|:---|:---|
|GET | /organizations | | [Response JSONlink](./jsons/Organization/all.json) | Get all the rows|
|GET | /organizations/{id} | | [Response JSONlink](./jsons/Organization/entity.json) | Get single row of given id |
|GET | /organizations/search | name=Synectiks | [Response JSONlink](./jsons/Organization/all.json) | Get all the rows on given filter|
|POST | /organizations | [Request JSONlink](./jsons/Organization/add.json) | [Response JSONlink](./jsons/Organization/entity.json) | Create a record|
|PATCH | /organizations/{id} | [Request JSONlink](./jsons/Organization/update.json) | [Response JSONlink](./jsons/Organization/entity.json) | Update a record|
|DELETE | /organizations/{id} | | | Delete a record|


## Department
| method | end point | Request | Response | Description | 
|:---|:---|:---|:---|:---|
|GET | /departments | | [Response JSONlink](./jsons/Department/all.json) | Get all the rows|
|GET | /departments/{id} | | [Response JSONlink](./jsons/Department/entity.json) | Get single row of given id |
|GET | /departments/search | name=IT Networki | [Response JSONlink](./jsons/Department/all.json) | Get all the rows on given filter|
|POST | /departments | [Request JSONlink](./jsons/Department/add.json) | [Response JSONlink](./jsons/Department/entity.json) | Create a record|
|PATCH | /departments/{id} | [Request JSONlink](./jsons/Department/update.json) | [Response JSONlink](./jsons/Department/entity.json) | Update a record|
|DELETE | /departments/{id} | | | Delete a record| 

## Cloud Environment
| method | end point | Request | Response | Description | 
|:---|:---|:---|:---|:---|
|GET | /cloud-environments | | [Response JSONlink](./jsons/CoudEnvironment/all.json) | Get all the rows|
|GET | /cloud-environments/{id} | | [Response JSONlink](./jsons/CoudEnvironment/entity.json) | Get single row of given id |
|GET | /cloud-environments/search | accountId=657907747 | [Response JSONlink](./jsons/CoudEnvironment/all.json) | Get all the rows on given filter|
|POST | /cloud-environments | [Request JSONlink](./jsons/CoudEnvironment/add.json) | [Response JSONlink](./jsons/CoudEnvironment/entity.json) | Create a record|
|PATCH | /cloud-environments/{id} | [Request JSONlink](./jsons/CoudEnvironment/update.json) | [Response JSONlink](./jsons/CoudEnvironment/entity.json) | Update a record|
|DELETE | /cloud-environments/{id} | | | Delete a record|


## Cloud Element Summary
| method | end point | Request | Response | Description | 
|:---|:---|:---|:---|:---|
|GET | /cloud-element-summary | | [Response JSONlink](./jsons/Cloud_Element_Summary/all.json) | Get all the rows|
|GET | /cloud-element-summary/{id} | | [Response JSONlink](./jsons/Cloud_Element_Summary/entity.json) | Get single row of given id |
|GET | /cloud-element-summary/search | accountId=657907747 | [Response JSONlink](./jsons/Cloud_Element_Summary/all.json) | Get all the rows on given filter|
|POST | /cloud-element-summary | [Request JSONlink](./jsons/Cloud_Element_Summary/add.json) | [Response JSONlink](./jsons/Cloud_Element_Summary/entity.json) | Create a record|
|PATCH | /cloud-element-summary/{id} | [Request JSONlink](./jsons/Cloud_Element_Summary/update.json) | [Response JSONlink](./jsons/Cloud_Element_Summary/entity.json) | Update a record|
|DELETE | /cloud-element-summary/{id} | | | Delete a record| 


## Cloud Element 
| method | end point | Request | Response | Description | 
|:---|:---|:---|:---|:---|
|GET | /cloud-elements | | [Response JSONlink](./jsons/Cloud_Element/all.json) | Get all the rows|
|GET | /cloud-elements/{id} | | [Response JSONlink](./jsons/Cloud_Element/entity.json) | Get single row of given id |
|GET | /cloud-elements/search | elementType=EC2 | [Response JSONlink](./jsons/Cloud_Element/all.json) | Get all the rows on given filter|
|POST | /cloud-elements | [Request JSONlink](./jsons/Cloud_Element/add.json) | [Response JSONlink](./jsons/Cloud_Element/entity.json) | Create a record|
|PATCH | /cloud-elements/{id} | [Request JSONlink](./jsons/Cloud_Element/update.json) | [Response JSONlink](./jsons/Cloud_Element/entity.json) | Update a record|
|DELETE | /cloud-elements/{id} | | | Delete a record| 

## Micro Service 
| method | end point | Request | Response | Description | 
|:---|:---|:---|:---|:---|
|GET | /micro-service | | [Response JSONlink](./jsons/Micro_Service/all.json) | Get all the rows|
|GET | /micro-service/{id} | | [Response JSONlink](./jsons/Micro_Service/entity.json) | Get single row of given id |
|GET | /micro-service/search | name=Admission&product=HR | [Response JSONlink](./jsons/Micro_Service/all.json) | Get all the rows on given filter|
|GET | /micro-service/enable-monitoring | name=Admission&product=HR | [Response JSONlink](./jsons/Micro_Service/enableMonitoring.json) | import all the dashboards for the services searched on given filter criteria |
|POST | /micro-service | [Request JSONlink](./jsons/Micro_Service/add.json) | [Response JSONlink](./jsons/Micro_Service/entity.json) | Create a record|
|PATCH | /micro-service/{id} | [Request JSONlink](./jsons/Micro_Service/update.json) | [Response JSONlink](./jsons/Micro_Service/entity.json) | Update a record|
|DELETE | /micro-service/{id} | | | Delete a record|  


## Deployment Environment 
| method | end point | Request | Response | Description | 
|:---|:---|:---|:---|:---|
|GET | /deployment-environments | | [Response JSONlink](./jsons/DeploymentEnvironment/all.json) | Get all the rows|
|GET | /deployment-environments/{id} | | [Response JSONlink](./jsons/DeploymentEnvironment/entity.json) | Get single row of given id |
|GET | /deployment-environments/search | elementType=EC2 | [Response JSONlink](./jsons/DeploymentEnvironment/all.json) | Get all the rows on given filter|
|POST | /deployment-environments | [Request JSONlink](./jsons/DeploymentEnvironment/add.json) | [Response JSONlink](./jsons/DeploymentEnvironment/entity.json) | Create a record|
|PATCH | /deployment-environments/{id} | [Request JSONlink](./jsons/DeploymentEnvironment/update.json) | [Response JSONlink](./jsons/DeploymentEnvironment/entity.json) | Update a record|
|DELETE | /deployment-environments/{id} | | | Delete a record|

## Catalogue 
| method | end point | Request | Response | Description | 
|:---|:---|:---|:---|:---|
|GET | /catalogue | | [Response JSONlink](./jsons/Catalogue/catalogue.json) | Get all the rows|
|GET | /catalogue/{id} | | [Response JSONlink](./jsons/Catalogue/catalogue.json) | Get single row of given id |
|POST | /catalogue | [Request JSONlink](./jsons/Catalogue/catalogue.json) | [Response JSONlink](./jsons/Catalogue/catalogue.json) | Create a record|
|PATCH | /catalogue/{id} | [Request JSONlink](./jsons/Catalogue/catalogue.json) | [Response JSONlink](./jsons/Catalogue/catalogue.json) | Update a record|
|DELETE | /catalogue/{id} | | | Delete a record|
|GET | /catalogue/datasource/{id} | | [Response JSONlink](./jsons/Catalogue/datasource/entity.json) | Get a datasource|
|GET | /catalogue/datasource/search | name=AWS-PullMetric-Api | [Response JSONlink](./jsons/Catalogue/datasource/all.json) | Get list of datasources on given filter|
|POST | /catalogue/datasource | [Request JSONlink](./jsons/Catalogue/datasource/add.json) | [Response JSONlink](./jsons/Catalogue/datasource/entity.json) | create a datasource|
|PATCH | /catalogue/datasource/{id} | [Request JSONlink](./jsons/Catalogue/datasource/update.json) | [Response JSONlink](./jsons/Catalogue/datasource/entity.json) | Update a datasource|
|GET | /catalogue/dasbhoard/{id} | | [Response JSONlink](./jsons/Catalogue/dashboard/entity.json) | Get a dashboard|
|GET | /catalogue/dasbhoard/search | associatedSLAType=PERFORMANCE | [Response JSONlink](./jsons/Catalogue/dashboard/all.json) | Get list of dashboards on given filter|
|POST | /catalogue/dashboard | [Request JSONlink](./jsons/Catalogue/dashboard/add.json) | [Response JSONlink](./jsons/Catalogue/dashboard/entity.json) | create a dashboard|
|PATCH | /catalogue/dashboard/{id} | [Request JSONlink](./jsons/Catalogue/dashboard/update.json) | [Response JSONlink](./jsons/Catalogue/dashboard/entity.json) | Update a dashboard| 
