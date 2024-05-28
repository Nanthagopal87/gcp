### Authentication and Authorization
- Oauth 2.0
- OpenId Connect(OIDC)
- IAP(Identity Aware Proxy)
- Cloud IAM
- Service Account

#

### Scenario1: Connect VM Instance to access data from Cloud Storage in same project

### Scenario2: Connect VM Instance in Project A to access data from Cloud Storage which in Project B


### Scenario3: From On-Prem Web Application to access images in Cloud Storage

#

### Scenario1: Connect VM Instance to access data from Cloud Storage in same project

- Create a new service account and provide permisssion to cloud storage(Provide least privilage)
- Assign the service account to VM Instance.

#
### Scenario2: Connect VM Instance in Project A to access data from Cloud Storage which in Project B

- Create a new Service account in Proect B and assign permission to access cloud storage.
- Assign that service account to VM Instance in Proect A

#
### Scenario3: From On-Prem Web Application to access images in Cloud Storage

- Create a service account with permission to access cloud storage
- Create a JSON key and share it.
- Create a environment variable in Local as
export GOOGLE_APP_CREDENTIALS=/path to the file
- From when we try to connect any google resoirces, it automatially looks for credentials(ADC) to environemnt variable.
