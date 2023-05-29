# Release 0.0.0.1
## CMDB APIs 
### Base API : http://34.199.12.114:6057/api
### 1. [CURD API End Points](./md-files/cmd-curd-apis.md)
| Entity | API End Point Document | 
|:---|:---|
|Organization | [URL](https://github.com/AppkubeCloud/appkube-architectures/blob/main/md-files/cmd-curd-apis.md#organization) |
|Department | [URL](https://github.com/AppkubeCloud/appkube-architectures/blob/main/md-files/cmd-curd-apis.md#department) |
|Cloud Environment (Landing Zone) | [URL](https://github.com/AppkubeCloud/appkube-architectures/blob/main/md-files/cmd-curd-apis.md#cloud-environment) |
|Cloud Element Summary | [URL](https://github.com/AppkubeCloud/appkube-architectures/blob/main/md-files/cmd-curd-apis.md#cloud-element-summary) |
|Cloud Element | [URL](https://github.com/AppkubeCloud/appkube-architectures/blob/main/md-files/cmd-curd-apis.md#cloud-element) |
|Micro Service | [URL](https://github.com/AppkubeCloud/appkube-architectures/blob/main/md-files/cmd-curd-apis.md#micro-service) |
|Deployment Environment | [URL](https://github.com/AppkubeCloud/appkube-architectures/blob/main/md-files/cmd-curd-apis.md#deployment-environment) |
|Catalogue | [URL](https://github.com/AppkubeCloud/appkube-architectures/blob/main/md-files/cmd-curd-apis.md#catalogue) |

### 2. Query API End Points
| method | end point | Request | Response | Description | 
|:---|:---|:---|:---|:---|
|GET | /organizations/{orgId}/cloud-environments/count | | [Response JSONlink](./jsons/\Cloud_Element_Summary/cloud-wise-resource-count.json) | count of landing zone and its associated assets, alerts and billing cost for each cloud of an organization |
|GET | /organizations/{orgId}/cloud/{cloud}/cloud-environments/count | | [Response JSONlink](./jsons/\Cloud_Element_Summary/single-cloud-resource-count.json) | count of landing zone and its associated assets, alerts and billing cost for given cloud of an organization |
|GET | /organizations/{orgId}/cloud-environments/summary | | [Response JSONlink](./jsons/\Cloud_Element_Summary/cloud-wise-product-list.json) | list of landing zone and its associated product enclaves, products, and app and data services for a given organization |
|GET | /organizations/{orgId}/cloud/{cloud}/cloud-environments/summary | | [Response JSONlink](./jsons/\Cloud_Element_Summary/single-cloud-wise-product-list.json) | list of landing zone and its associated product enclaves, products, and app and data services for a given organization and cloud |