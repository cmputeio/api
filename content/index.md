---
weight: 10
title: API Reference
---

# Introduction

Welcome to the cmpute.io API Portal. Here you will find what you need to quickly start using cmpute.io. You can use this API to access all our API endpoints. It provides descriptions, syntax, and usage examples for each of the actions and data types used. 

Currently we support the following official client bindings:

* **Shell**


# Overview
Each customer of cmpute gets their own customized URL for access. Using the web console, you can generate new set of API access keys. You need to safe keep the keys.

The API is organized around REST. All requests should be made over SSL. All request and response bodies, including errors, are encoded in JSON.

**Note-cmpute API SDK doesn’t send the secret key in any request.** 

# Authentication

cmpute.io supports two types of API authentication mechanism:

1. **HMAC** which validates calls using request signature 

2. **API Key** based authentication

Before making calls to the API, setup the base URI or cmpute.io account. You can get the access key and secret key in the [cmpute account](https://join.cmpute.io).

**End Point**

To call API requests to cmpute .io, please send HTTP(S) post requests to:

`https://<customerdomain>.cmpute.io/api/`

**APIKey**

APIKey is a  user's unique authentication key string. This authentication key can be generated in your cmpute.io account settings. This key is mandatory and needs to be sent as part of every API call. The Key should be sent along in the Request Header as below.

`Authorization: ApiKey AccessKey:SecretKey`


# API Definition
cmpute.io API supports the following entities:


* Accounts
* Jobs
* Runs
	* Instances

# Accounts API

Attach your AWS account to cmpute using the accounts API. Accounts calls allow you to create, edit or view AWS accounts associated with your cmpute account.

## Get All AWS accounts
>To get all aws accounts

```shell

curl "http://<customer.cmpute.io>/api/accounts"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell
{
	"RequestId": "<string>",
	"Data": {
		"ActiveProcessorCount": float,
		"Platform": "<string>",
		"PlatformName": "<string>",
		"BaseRegion": "<string>",
		"MaxRIPercentageToUse": float,
		"RoleArn": "<tsring>",
		"Teams": ["<string>", "<string>"],
		"Id": "<string>",
		"Name": "<string>"
	}, 	
	"Errors": {},
	"ContinuationToken": null
}

```

>Example

```shell
{
	"RequestId": "9a5741cf-dd15-49fa-8944-1bfaa543ad5a",
	"Data": {
		"ActiveProcessorCount": 0.0,
		"Platform": "AmazonWebServices",
		"PlatformName": "Amazon Web Services",
		"BaseRegion": "us-east-1",
		"MaxRIPercentageToUse": 0.0,
		"RoleArn": "arn:aws:iam::xxxxxxxxxxxx:role/test/test-trusted-role",
		"Teams": ["Organization"],
		"Id": "A-7EADA1xx",
		"Name": "Test"
	}, 	
	"Errors": {},
	"ContinuationToken": null
}

```


GET HTTP Method to get all AWS accounts associated with your cmpute account

**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/accounts`</b>


### **Attributes**

Parameter |Data Type |Description
--------- | -------  | -------------
ActiveProcessorCount |Int |
BaseRegion | String  | Availability Zones associated with the account
ID |String|Account ID
MaxRIPercentageToUse|Float|Maximum reserved instance
Platform|String| Cloud platform supported
PlatformName|String|Cloud Platform Name
RoleArn|String|Amazon web services Role Amazon Resource Name
Teams|String Array[]|Teams associated to an account. By default all accounts are assocuated with team 'Organization'

<aside class=  "success">
Account List retrieved successfully
</aside>

## Get specific AWS account details
>To get details of a specifc aws accounts

```shell

curl "http://<customer.cmpute.io>/api/{account ID}" 
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell
{
	"RequestId": "<string>",
	"Data": {
		"ActiveProcessorCount": float,
		"Platform": "<string>",
		"PlatformName": "<string>",
		"BaseRegion": "<string>",
		"MaxRIPercentageToUse": float,
		"RoleArn": "<tsring>",
		"Teams": ["<string>", "<string>"],
		"Id": "<string>",
		"Name": "<string>"
	}, 	
	"Errors": {},
	"ContinuationToken": null
}

```

GET HTTP Method to get the AWS account details related to the specified account ID 

**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/accounts/{account ID}`</b>

### **Attributes**

Parameter |Data Type |Description
--------- | -------  | -------------
ActiveProcessorCount |Int |
BaseRegion | String  | Availability Zones associated with the account
ID |String|Account ID
MaxRIPercentageToUse|Float|Maximum reserved instances
Platform|String| Cloud platform supported
PlatformName|String|Cloud Platform Name
RoleArn|String|Amazon web services Role Amazon Resource Name
Teams|String Array[]|Teams associated to an account. By default all accounts are assocuated with team 'Organization'

<aside class=  "success">
Account details retrieved successfully
</aside>

## Add a new AWS account 
>To add a new aws account

```shell

curl "http://<customer.cmpute.io>/api/CloudFrontAWS" 
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

{
	"RequestId": "<string>",
	"Data": {
		"ActiveProcessorCount": float,
		"Platform": "<string>",
		"PlatformName": "<string>",
		"BaseRegion": "<string>",
		"MaxRIPercentageToUse": float,
		"RoleArn": "<tsring>",
		"Teams": ["<string>", "<string>"],
		"Id": "<string>",
		"Name": "<string>"
	}, 	
	"Errors": {},
	"ContinuationToken": null
}

```

POST HTTP Method to add a new AWS account to your cmpute account


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/accounts/CloudFrontAWS`</b>


### **Query Parameters**

Parameter |Data Type |Description
--------- | -------  |-------------
BaseRegion | String  | Availability Zones associated with the account
Name|String|Account Name
RoleArn|String|Amazon web services Role Amazon Resource Name
Teams|String Array[]|Team(s) associated to an account

<aside class=  "success">
Account details successfully created
</aside>


## Update an AWS account 
>To update details of an existing AWS acoount

```shell

curl "http://<customer.cmpute.io>/api/{account ID}" 
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

{
	"RequestId": "<string>",
	"Data": {
		"ActiveProcessorCount": float,
		"Platform": "<string>",
		"PlatformName": "<string>",
		"BaseRegion": "<string>",
		"MaxRIPercentageToUse": float,
		"RoleArn": "<tsring>",
		"Teams": ["<string>", "<string>"],
		"Id": "<string>",
		"Name": "<string>"
	}, 	
	"Errors": {},
	"ContinuationToken": null
}

```

PUT HTTP Method to update the details of an AWS account


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/accounts/{account ID}`</b>


### **Query Parameters**

Parameter |Data Typev| Description
--------- | -------  | -------------
BaseRegion | String  | Availability Zone associated with the account
Name |String|Account Name
Teams|String Array[]|Team(s) associated to the account

<aside class=  "success">
Account details successfully updated
</aside>

## Delete an AWS account 
>To delete an existing AWS account

```shell

curl "http://<customer.cmpute.io>/api/accounts/{account ID}" 
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:


```shell

{
	"RequestId": "<string>",
	"Data": boolean,
	"Errors": {},
	"ContinuationToken": null
}
```
>Example

```shell
{
	"RequestId": "a22a18df-a428-4866-bc65-e250880d629b",
	"Data": true,
	"Errors": {},
	"ContinuationToken": null
}
```

DELETE HTTP Method to delete an AWS account


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/accounts/{account ID}`</b>


### **Query Parameters**

Parameter |Data Type | Description
--------- | -------  | -------------
Account ID |String|AWS account ID

<aside class=  "success">
AWS Account is successfully deleted
</aside>


# Users API

## Get All Users
>To get a list of all Users created in the cmpute account

```shell

curl "http://<customer.cmpute.io>/api/users"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

  {
	"RequestId": "<string>",
	"Data": {
		"UserName": "<string>",
		"FullName": "<string>",
		"Role": "<string>",
		"Id": Int
	}, 
	"Errors": {},
	"ContinuationToken": null
}
```

>Example

```shell
{
	"RequestId": "c6d7bd0b-9088-4069-b44b-33154faa80ca",
	"Data": {
		"UserName": "test@batch.ly",
		"FullName": "Admin",
		"Role": "Administrator",
		"Id": 89
	}, 
	"Errors": {},
	"ContinuationToken": null
}

```

GET HTTP Method to get all Users created in your cmpute account

**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/users`</b>


### **Attributes**

Parameter |Data Type |Description
--------- | -------  |-------------
User Name| String  |Email ID of the user
Full Name |String|Name of the user
Role|String| User Role
ID|Int|User ID


<aside class=  "success">
User List retrieved successfully
</aside>


## Get specific user details
> To get user details for a specific user ID 

```shell

curl "http://<customer.cmpute.io>/api/users/{user ID}"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

{
	"RequestId": "<string>",
	"Data": {
		"UserName": "<string>",
		"FullName": "<>string",
		"Role": "<string>",
		"Id": Int
	},
	"Errors": {},
	"ContinuationToken": null
}

```

GET HTTP Method to get details of a specific user in the cmpute account

**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/users/<user ID>`</b>



### **Query Parameter**

Parameter |Data Type |Description
--------- | -------  | -------------
User ID|Int|


<aside class=  "success">
User details retrieved successfully
</aside>

## Add a new User
> To add a new user in the cmpute account

```shell

curl "http://<customer.cmpute.io>/api/users"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

 {
	"RequestId": "<string>",
	"Data": boolean,
	"Errors": {},
	"ContinuationToken": null
}

```

POST HTTP Method to add a new user to the cmpute account

**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/users/`</b>


### **Query Parameter**

Parameter |Data Type |Description
--------- | -------  |-------------
User Name| String  |Email ID of the user
Full Name |String|Name of the user
Role|String| User Role

<aside class=  "success">
New user created successfully
</aside>


## Update user details
> To update details of a specific user

```shell

curl "http://<customer.cmpute.io>/api/users/{user ID}"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell
{
	"RequestId": "<string>",
	"Data": boolean,
	"Errors": {},
	"ContinuationToken": null
}
```

PUT HTTP Method to update User details created in the cmpute account

**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/users/{user ID}`</b>


### **Query Parameter**

Parameter |Data Type |Description
--------- | -------  |-------------
User Name| String  |Email ID of the User
Full Name |String|Name of the User
Role|String|User role
ID|Int|User ID


<aside class=  "success">
User details updated successfully
</aside>


## Get User's Team(s)  
>To get the list of team(s) a user belongs to

```shell

curl "http://<customer.cmpute.io>/api/v2/Users/Teams"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell
{
	"Teams": {
		"Id": "<string>",
		"IsDefault": boolean,
		"Description": "<string>",
		"Name": "<string>"
	}
```
>Example

```shell
{
	"Teams": {
		"Id": "Z-7EA3AF3D",
		"IsDefault": false,
		"Description": Test Team,
		"Name": "Test"
    }
	,
	"ContinuationToken": null,
	"RequestId": "fc15a09x-f3a9-4xx4-aaf2-7658195a5afe",
	"Errors": {}
}

```
GET HTTP Method to get the list of team(s) the user belongs to

**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/Users/Teams`</b>

### **Attributesr**

Parameter |Data Type |Description
--------- | -------  |-------------
ID|Int|User ID
Is Default|boolean|User role
Descriptipon| String  |
Name |String|Team Name

<aside class=  "success">
User's team list retrieved successfully
</aside>

# Teams API

## Get All Teams
>To get a list of all Teams created in the cmpute account

```shell

curl "http://<customer.cmpute.io>/api/v2/Teams"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

{
	"Teams": {
		"Id": "<string>",
		"IsDefault": boolean,
		"Description": "<string>",
		"Name": "<string>"
	},
	"ContinuationToken": null,
	"RequestId": "0b066b2c-5c38-4d3e-8172-9244ccbfc602",
	"Errors": {}
}

```

```shell

{
	"Teams": [{
		"Id": "Z-7EA3AFXX",
		"IsDefault": false,
		"Description": Test Team,
		"Name": "Test Team"
	}, {
		"Id": "Z-XXXXXXXX",
		"IsDefault": true,
		"Description": null,
		"Name": "Organization"
	}],
	"ContinuationToken": null,
	"RequestId": "0b066b2c-5c38-4d3e-8172-9244ccbfc602",
	"Errors": {}
}

```

GET HTTP Method to get all Teams created in the cmpute account

**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/Teams`</b>


### **Attributes**

Parameter |Data Type | Description
--------- | -------  |-------------
Description| String  |Team description
ID |String|Team ID
IsDefault|Boolean|
Name|String|Team Name


<aside class=  "success">
Team List retrieved successfully
</aside>

## Get specific Team details
>To get details of a specifc team in your cmpute account

```shell

curl "http://<customer.cmpute.io>/api/v2/Teams/{team ID}"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```

>The above command returns JSON structured like this:

```shell

{
	"Team": {
		"IsDefault": boolean,
		"Description": "<string>",
		"Name": "<string>"
	},
	"RequestId": "<string>",
	"Errors": {}
}

```

GET HTTP Method to get details of a specific team

**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/Teams/{team ID}`</b>


### **Attributes**

Parameter |Data Type | Description
--------- | -------  |-------------
Team ID|Int|


<aside class=  "success">
Team details retrieved successfully
</aside>

## Add a new Team 
>To add a new Team

```shell

curl "http://<customer.cmpute.io>/api/v2/Teams"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

{
	"Success": boolean,
	"RequestId": "<string>",
	"Errors": {}
}

```

POST HTTP Method to create a new Team in your cmpute account


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/Teams`</b>


### **Query Parameters**

Parameter |Data Type | Description
--------- | -------  | -------------
Description| String  | Team description
Name|String|Team Name

<aside class=  "success">
Team created successfully 
</aside>


## Update Team Details 
>To update details of a team

```shell

curl "http://<customer.cmpute.io>/api/v2/Teams/{team ID}"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

{
	"Success": boolean,
	"RequestId": "<string>",
	"Errors": {}
}

```

PUT HTTP Method to update the details of a team


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/Teams/{team ID}`</b>

### **Query Parameters**

Parameter |Data Type |Description
--------- | -------  |-------------
ID|String|Team ID
Description|String|Team description
Name|String|Team Name

<aside class=  "success">
Team details updated successfully 
</aside>


## Delete a Team   
>To delete a team from your cmpute account

```shell

curl "http://<customer.cmpute.io>/api/v2/Teams/{team ID}"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

{
	"Success": boolean,
	"RequestId": "<string>",
	"Errors": {}
}

```
DELETE HTTP Method to delete an AWS account


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/Teams/{team ID}`</b>


### **Query Parameters**

Parameter |Data Type |Description
--------- | -------  |-------------
ID |String|Team ID

<aside class=  "success">
Team is successfully deleted
</aside>


## Get User(s) of a Team
>To get the list of users in a team

```shell
curl "http://<customer.cmpute.io>/api/v2/Teams/Test%20Teams/Users"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

{
	"Users": [{
		"UserName": "f@f.com",
		"Email": "f@f.com",
		"DisplayName": "fefs"
	}, {
		"UserName": "sand@cmpute.io",
		"Email": "sand@cmpute.io",
		"DisplayName": "Sandy1"
	}],
	"ContinuationToken": null,
	"RequestId": "5227da64-6a12-4c9a-942a-8c9b7de36954",
	"Errors": {}
}

```
>Example

```shell

{
	"Users": [{
		"UserName": "test@batchly.com",
		"Email": "test@batchly.com",
		"DisplayName": "Test"
	}, {
		"UserName": "Test@cmpute.io",
		"Email": "Test@cmpute.io",
		"DisplayName": "Testing"
	}],
	"ContinuationToken": null,
	"RequestId": "5227xx64-6a12-4cxx-942a-8c9b7xx36954",
	"Errors": {}
}

```

GET HTTP Method to get the list of User(s) in a Team


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/Teams/Test%20Teams/Users`</b>


### **Attributes**

Parameter |Data Type |Description
--------- | -------  |-------------
User Name |String|Email ID of the user
Email |String|Email ID of the user
Display Name|String|User Name


<aside class=  "success">
Team user list rretrieved successfully 
</aside>

## Add User(s) to a Team   
>To attach a user to a team in your cmpute account

```shell

curl "http://<customer.cmpute.io>/api/v2/Teams/Test%20Teams/Users"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

{
	"Success": boolean,
	"RequestId": "<string>",
	"Errors": {}
}

```
ADD HTTP Method to add User(s) to a Team


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/Teams/Test%20Teams/Users`</b>


### **Query Parameters**

Parameter |Data Type |Description
--------- | -------  |-------------
User Name |String|Email ID of the user


<aside class=  "success">
User(s) added to the team successfully
</aside>



# Jobs API

Jobs are calls to perform various operations on the actual dataset. This call varies from one application to another. Though it is application specific, each job requires a Job Name, Project, SLA, input location and output location to be mentioned.

CMPUTE responds immediately with a job ID so your application can track the progress of the job. 

CMPUTE works through Apps. There are marketplace apps such as ASG from AWS, FFMpeg for video transcoding, and JMeter for load testing. You may also upload your own private app to run in your cmpute account.

Nevertheless, each app has its own set of APIs to perform the basic operations.

Below is a list of Job API's which are common across all apps

## Get all Regions 
>To get the list of all regions or availability zones

```shell

curl "http://<customer.cmpute.io>/api/api/caches/regions?platform={platform ID}"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell
{
	"RequestId": "<string>",
	"Data": {
		"Id": "<string>",
		"Name": "<string>"
	}
}	
```
>Example

```shell
{
	"RequestId": "<string>",
	"Data": [{
		"Id": "ap-south-1",
		"Name": "Asia Pacific (Mumbai)"
	}, {
		"Id": "ap-northeast-2",
		"Name": "Asia Pacific (Seoul)"
	},
```


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/api/caches/regions?platform={platform ID}`</b>


### **Attributes**

Parameter |Data Type | Default | Description
--------- | -------  | ---------|-------------
Platform ID |Int||Example:- Amazon etc..


<aside class=  "success">
Region List is retrieved successfully 
</aside>




## Get all Jobs 
>To get the list of all jobs created in your cmpute account

```shell

curl "http://<customer.cmpute.io>/api/jobs"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

{
	"RequestId": "<string>",
	"Data": {
		"Runs": float,
		"IsScheduled": boolean,
		"IsExecuting": boolean,
		"Engine": "<string>",
		"AppName": "<string>",
		"IsPrivateApp": boolean,
		"Id": "<string>",
		"Name": "<string>"
	}
}	
```

>Example

```shell
{
	"RequestId": "cdede42e-7171-45b0-9784-854e1f6e8fbe",
	"Data": {
		"Runs": 2.0,
		"IsScheduled": false,
		"IsExecuting": true,
		"Engine": "Cluster",
		"AppName": "Auto Scaling Group",
		"IsPrivateApp": false,
		"Id": "W-05XXIXXX",
		"Name": "API_Job"
	}
}
```


GET HTTP Method lists all Jobs created in the cmpute account


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/jobs`</b>


### **Attributes**

Parameter |Data Type | Description
--------- | -------  | -------------
ID |String|Job ID
Name|String|Job Name
AppName|String|Application used to run the job
Runs|Int|Number of times the job is run till date
IsExecuting|Boolean|This will be set to true if the job is currently running else false
IsPrivateApp|Boolean|This will be set to true if the job is running on a private application(other than AWS Apps)
IsScheduled|Boolean|This will be set to true of the job is scheduled to run

<aside class=  "success">
Job list is successfully retrieved
</aside>



# Auto Scaling Group API


## ASG List
>To get a list of all ASG's created in your AWS account

```shell

curl "http://<customer.cmpute.io>/api/Accounts/{account ID}/AutoScalingGroups?region={region ID}"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

{
{
	"RequestId": "d7610a8b-1118-43dc-9f14-ce0a0525c88b",
	"Data": [{
		"Id": "<string>",
		"Name": "<string>"
	}	
	"Errors": {},
	"ContinuationToken": null
}
}

```

>Example

```shell
{
	"RequestId": "a816dxxx-78fc-4x65-9bxx-9b8796f6acb4",
	"Data": [{
		"Id": "ASG-Test",
		"Name": "ASG-Test"
	}


```

GET HTTP Method lists all ASG's created in your AWS account


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/{account ID}/AutoScalingGroups?region={region ID}`</b>


### **Query Parameter**

Parameter |Data Type |Description
--------- | -------  | -------------
Account ID||cmpute genertaed AWS account ID  
Region ID |String||Availability Zone

<aside class=  "success">
ASG list is successfully retrieved
</aside>


## Get specific ASG details
>To get details of a specific ASG

```shell

curl "http://<customer.cmpute.io>/api/Accounts/{account ID}/AutoScalingGroups/{ASG Name}?region={region ID}"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

{
	"RequestId": "20509936-f9a2-48e7-ad96-4a81acabc918",
	"Data": {
		"AutoScalingGroup": {
			"Name": "<string>",
			"MinCount": int,
			"MaxCount": int,
			"DesiredCount": int,
			"VPCId": "<string>",
			"LaunchConfigurationName": "<ASG Name>",
			"LoadBalancerNames": ["<Load Balancer Name>"],
			"SubnetList": ["<string>", "<string>"],
			"ActiveInstances": [int],
			"HealthCheckGracePeriod": float,
			"DefaultCooldown": int,
			"Tags": {
				"Name": "<string>"
			},
			"AvailabilityZones": ["<string>", "<string>"],
			"PlacementGroup": null,
			"TargetGroupARNs": []
		},
		"LaunchConfiguration": {
			"Name": "<string>",
			"InstanceType": "<string>",
			"AmiId": "<string>",
			"UserData": null,
			"KeyName": "<string>",
			"IamInstanceProfile": null,
			"SecurityGroups": ["<string>"],
			"AssociatePublicIpAddress": boolean,
			"BlockDeviceMappings": [{
				"DeviceName": "<string>",
				"Ebs": {
					"DeleteOnTermination": boolean,
					"Encrypted": boolean,
					"Iops": int,
					"SnapshotId": "<string>",
					"VolumeSize": int,
					"VolumeType": {
						"Value": "<string>"
					}
				},
				"NoDevice": null,
				"VirtualName": null
			}],
			"EbsOptimized": boolean,
			"KernelId": null,
			"RamDiskId": null,
			"PlacementTenancy": null
		},
		"LoadBalancers": {
			"LB-guru": {
				"IsClassic": true,
				"SubnetList": ["<string>", "<string>"],
				"VPCId": "<string>",
				"Name": "<string>",
				"TargetGroupArn": null,
				"Port": 0,
				"HealthCheckUnhealthyThreshold": int,
				"HealthCheckHealthyThreshold": int,
				"HealthCheckInterval": int,
				"HealthCheckTimeout": int,
				"ConnectionDrainingEnabled": boolean,
				"ConnectionDrainingTimeout": int,
				"AvailabilityZones": ["<string>", "<string>"]
			}
		},
		"TargetGroupARNsDetail": null,
		"Queues": null,
		"Triggers": null
	},
	"Errors": {},
	"ContinuationToken": null
}

```
>Example
```shell
{
	"RequestId": "c4307fa4-c48e-4b30-b6a1-57b10dfe1fe9",
	"Data": {
		"AutoScalingGroup": {
			"Name": "ASG-Test",
			"MinCount": 1,
			"MaxCount": 1,
			"DesiredCount": 1,
			"VPCId": "vpc-xxxxxxxxx",
			"LaunchConfigurationName": "test_dev",
			"LoadBalancerNames": ["LB-test"],
			"SubnetList": ["subnet-xxxxxxxx"],
			"ActiveInstances": [],
			"HealthCheckGracePeriod": 0.0,
			"DefaultCooldown": 300,
			"Tags": {
				"Name": "ELB-Test"
			},
			"AvailabilityZones": ["us-east-1a"],
			"PlacementGroup": null,
			"TargetGroupARNs": []
		},
		"LaunchConfiguration": {
			"Name": "test_dev",
			"InstanceType": "t1.micro",
			"AmiId": "ami-xxxxxxxx",
			"UserData": null,
			"KeyName": "Test-KP",
			"IamInstanceProfile": null,
			"SecurityGroups": ["sg-xxxxxxxx"],
			"AssociatePublicIpAddress": false,
			"BlockDeviceMappings": [{
				"DeviceName": "/dev/xxxx",
				"Ebs": {
					"DeleteOnTermination": true,
					"Encrypted": false,
					"Iops": 0,
					"SnapshotId": "snap-xxxxxxxxxxxxx",
					"VolumeSize": 8,
					"VolumeType": {
						"Value": "standard"
					}
				},
				"NoDevice": null,
				"VirtualName": null
			}],
			"EbsOptimized": false,
			"KernelId": null,
			"RamDiskId": null,
			"PlacementTenancy": null
		},
		"LoadBalancers": {
			"LB-guru": {
				"IsClassic": true,
				"SubnetList": ["subnet-xxxxxxxx"],
				"VPCId": "vpc-xxxxxxx",
				"Name": "LB-test",
				"TargetGroupArn": null,
				"Port": 0,
				"HealthCheckUnhealthyThreshold": 2,
				"HealthCheckHealthyThreshold": 10,
				"HealthCheckInterval": 30,
				"HealthCheckTimeout": 5,
				"ConnectionDrainingEnabled": true,
				"ConnectionDrainingTimeout": 300,
				"AvailabilityZones": ["us-east-1a"]
			}
		},
		"TargetGroupARNsDetail": null,
		"Queues": null,
		"Triggers": null
	},
	"Errors": {},
	"ContinuationToken": null
}
```

GET HTTP Method will get details of a specific ASG created in your AWS account

**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/Accounts/{account ID}/AutoScalingGroups/{ASG Name}?region={region ID}`</b>
### **Query Parameter**

Parameter |Data Type |Description
--------- | -------  | -------------
Account ID||cmpute genertaed AWS account ID  
Region ID |String|Availability Zone
ASG Name|string|ASG Name	

<aside class=  "success">
ASG details successfully retrieved
</aside>

## Get details of an ASG Job
>To get details of an ASG job created in your cmpute account

```shell

curl "http://<customer.cmpute.io>/api/api/v2/apps/AutoScalingGroup/{ASG job ID}"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

{
	"Job": {
		"AccountName": "<string>",
		"SuspendScalingOperations": boolean,
		"StandBy": boolean,
		"AccountId": "<string>",
		"BaseRegion": "<string>",
		"Name": "<string>",
		"AutoScalingGroupName": "<string>",
		"MinOnDemandInstanceCount": int,
		"RestrictToSelectedInstance": boolean,
		"ReplaceUnhealthyInstances": boolean,
		"ReinstateOnStop": boolean
	},
	"RequestId": "<string>",
	"Errors": {}
}

```
GET HTTP Method will get details of a specific ASG job created in your cmpute account


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/apps/AutoScalingGroup/{ASG job ID}`</b>

### **Query Parameter**

Parameter |Data Type |Description
--------- | -------  | -------------
Account ID|String|cmpute genertaed AWS account ID in which the ASG job should run 
AutoScalingGroupName|string|ASG name created in customer AWS account

<aside class=  "success">
ASG Job details retrieved successfully
</aside>


## Create an ASG Job
>To create a new ASG job 

```shell

curl "http://<customer.cmpute.io>/api/v2/apps/AutoScalingGroup/Add"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell
{
      	{
	"Job": {
		"Runs": float,
		"IsScheduled": boolean,
		"IsExecuting": boolean,
		"Engine": "<string>",
		"AppName": "<string>",
		"IsPrivateApp": boolean,
		"Id": "<string>",
		"Name": "<string>"
	},
	"RequestId": "<string>",
	"Errors": {}
}
}
```
>Example

```shell
{
      	{
	"Job": {
		"Runs": 0.0,
		"IsScheduled": false,
		"IsExecuting": false,
		"Engine": "Cluster",
		"AppName": "Auto Scaling Group",
		"IsPrivateApp": false,
		"Id": "W-8F7137AA",
		"Name": "ASG Job"
	},
	"RequestId": "cbf34f9d-2cc8-4056-aad6-0646e1d1xxc9",
	"Errors": {}
}
}
```

POST HTTP Method creates a new ASG job

**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/apps/AutoScalingGroup/Add`</b>


### **Query Parameters**
Parameter |Data Type |Description
--------- | -------  | -------------
Account ID|String|cmpute genertaed AWS account ID in which the ASG job should run 
AutoScalingGroupName|string|ASG name created in customer AWS account
BaseRegion|string|Availability Zone where the job is required to run
MinOnDemandInstanceCount|Int|
Name|String|ASG Job Name
ReinstateOnStop|Boolean|
ReplaceUnhealthyInstances|Boolean|
RestrictToSelectedInstance|Boolean|


<aside class=  "success">
ASG Job created successfully 
</aside>



## Update an ASG Job
>To update the details of an job in your cmpute account

```shell

curl "http://<customer.cmpute.io>/api/v2/apps/AutoScalingGroup/{ASG job ID}"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```

>The above command returns JSON structured like this:

```shell
{
	"Job": {
		"Runs": float,
		"IsScheduled": boolean,
		"IsExecuting": boolean,
		"Engine": "<string>",
		"AppName": "<string>",
		"IsPrivateApp": boolean,
		"Id": "<string>",
		"Name": "<string>"
	},
	"RequestId": "<string>",
	"Errors": {}
}

```
>Example

```shell
{
	"Job": {
		"Runs": 0.0,
		"IsScheduled": false,
		"IsExecuting": false,
		"Engine": "Cluster",
		"AppName": "Auto Scaling Group",
		"IsPrivateApp": false,
		"Id": "W-34111x47",
		"Name": "Job_Name"
	},
	"RequestId": "335e8ex4-14c8-xdd4-a7db-f7380654xx17",
	"Errors": {}
}
```
PUT HTTP Method updates the details of a specific ASG job

**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/apps/AutoScalingGroup/{ASG job ID}`</b>


### **Query Parameters**
Parameter |Data Type |Description
--------- | -------  | -------------
MinOnDemandInstanceCount|Int|Minimum number of instances to be launched
Name|String|ASG Job Name
ReinstateOnStop|Boolean|
ReplaceUnhealthyInstances|Boolean|Replaces unhealthy instances if any
RestrictToSelectedInstance|Boolean|Restrict not to choose instances other than selected instances
StandBy|boolean|suspends all operations such as scaling, swapping instances, replacing instances etc...
SuspendScalingOperations|boolean| suspends only scaling operations


<aside class=  "success">
ASG Job details updated successfully 
</aside>



## Delete an ASG Job 
>To delete an ASG job from your cmpute account

```shell

curl "http://<customer.cmpute.io>/api/v2/apps/AutoScalingGroup/{ASG job ID}"
  -H "Authorization: ApiKey AccessKey:SecretKey"


```

>The above command returns JSON structured like this:

```shell

{
	"IsDeleted": boolean,
	"RequestId": "<string>",
	"Errors": {}
}
	
```

DELETE HTTP Method deletes an ASG job from the cmpute account


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/apps/AutoScalingGroup/{ASG job ID}`</b>

### **Query Parameter**

Parameter |Data Type | Default | Description
--------- | -------  | ---------|-------------
ID |String||Job ID

<aside class=  "success">
ASG Job is deleted successfully 
</aside>



## Execute an ASG Job 
>To execute an ASG job from your cmpute account

```shell

curl "http://<customer.cmpute.io>/api/v2/apps/AutoScalingGroup/{job ID}/execute"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell
{
	"RunRequestId": "<string>",
	"RequestId": "<string>",
	"Errors": {}
}
```
>Example

```shell
{
	"RunRequestId": "xxec631d-42e5-49a7-9138-41693xx403d7",
	"RequestId": "x67048e2-2e46-4a94-9x6x-x6e61d7285c7",
	"Errors": {}
}

```

>The 'Run Request ID' returned above is used as a parameter to get the Job Run ID

```shell

curl "http://<customer.cmpute.io>/api/runs/Check/'{Run Request ID}"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

{
	"RequestId": "<string>",
	"Data": "<string>",
	"Errors": {},
	"ContinuationToken": null
}

```
>Example

```shell
{
	"RequestId": "40e1a96x-29a6-446c-9220-0xx797c1xxx1",
	"Data": "R-xxD84C58",
	"Errors": {},
	"ContinuationToken": null
}

```


Executing a job is a 2 step process.

<b> Step 1 </b> - Begins the execution process

POST HTTP method excutes an ASG job from your cmpute account

**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/apps/AutoScalingGroup/{job ID}/execute`</b>

### **Query Parameter**

Parameter |Data Type |Description
--------- | -------  |-------------
Job ID |String|ASG Job ID

<b> Step 2 </b> - Gets the job Run ID

GET HTTP method gets the job execution Run ID 

**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/runs/Check/'{Run Request ID}`</b>

### **Query Parameter**

Parameter |Data Type |Description
--------- | -------  |-------------
RunRequestId |String|Output returned in step1 

<aside class=  "success">
ASG Job is executed successfully 
</aside>

## Stop an ASG Job 
>To stop an ASG job in your cmpute account

```shell

curl "http://<customer.cmpute.io>/api/runs/{run ID}"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell
{
	"RequestId": "<string>",
	"Data": boolean,
	"Errors": {},
	"ContinuationToken": null
}

```

>Example

```shell
{
	"RequestId": "ecee80xx-57c6-4990-8ex6-a7c381286xx4",
	"Data": true,
	"Errors": {},
	"ContinuationToken": null
}
```

PUT HTTP Method stops an ASG job run from the cmpute account


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/runs/{run ID}"`</b>

### **Query Parameter**

Parameter |Data Type |Description
--------- | -------  |-------------
ID |String||Run ID


<aside class=  "success">
ASG Job is stopped successfully 
</aside>


# Runs API
Runs are individual instances of the job in cmpute . Runs API allows you to get run summary, instance details and run logs alongwith RightSizing recommendations. 

<aside class=  "notice">
The API's defined below are common for all job types
</aside>

## Get Run Summary Details
>To get the Job run summary details

```shell

curl "http://<customer.cmpute.io>/api/v2/runs/{Run ID}}/summary"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell
{
	"RunSummary": {
		"AppName": "<string>",
		"JobName": "<string>",
		"JobId": "<string>",
		"Status": "<string>",
		"RunDate": "<DateTime>",
		"EndDate": "<DateTime>",
		"ActualCost": float,
		"ActualSavings": float,
		"EstimatedCost": float,
		"EstimatedSavings": float,
		"SavingsPercentage": float,
		"SpotHours": float,
		"OnDemandHours": float,
		"IsPrivateApp": boolean
	},
	"RequestId": "<string>",
	"Errors": {}
}

```

>Example

```shell
{
	"RunSummary": {
		"AppName": "Auto Scaling Group",
		"JobName": "API_Job",
		"JobId": "W-0521B521",
		"Status": "Processing",
		"RunDate": "23 Jun 2017, 05:48",
		"EndDate": null,
		"ActualCost": 100.00,
		"ActualSavings": 75.00,
		"EstimatedCost": 100.00,
		"EstimatedSavings": 75.00,
		"SavingsPercentage": 75.00,
		"SpotHours": 4.5,
		"OnDemandHours": 1.0,
		"IsPrivateApp": false
	},
	"RequestId": "8464760a-0axx-401c-88xx-e895c0193fb9",
	"Errors": {}
}

```

GET HTTP Method gets the job run summary details 


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/runs/{Run ID}/summary"`</b>

### **Query Parameter**

Parameter |Data Type |Description
--------- | -------  |-------------
RunID |String|Job Run ID


<aside class=  "success">
Job run Instance details retreievd successfully 
</aside>

## Get Run Instance Details
>To get the Job run instance details

```shell

curl "http://<customer.cmpute.io>/api/runs/{Run ID}/Instances"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

{
	"RequestId": "36e6ae68-1a42-4441-8102-f6eb4c3a7eab",
	"Data": [{
		"ELBHealthCheck": [{
			"Name": "jayaa_dev_09_06_2017",
			"HealthCheckStatus": "Healthy",
			"HealthCheckDescription": "instance is registered"
		}],
		"IsHealthy": true,
		"ELBHealthCheckDetailsAsString": "Healthy - instance is registered behind jayaa_dev_09_06_2017",
		"InstanceId": "i-02b315e6afbe78876",
		"InstanceType": "t1.micro",
		"SubnetId": "subnet-aac48781",
		"AvailabilityZone": "us-east-1c",
		"LifeCycle": null,
		"Status": "running",
		"LaunchTime": "Friday 23 Jun 2017 05:50:15",
		"PrivateIpAddress": "172.31.49.28",
		"Name": null,
		"StopTime": null,
		"Distribution": "None"
	}],
	"Errors": {},
	"ContinuationToken": null
}

```

>Example

```shell

{
	"RequestId": "36e6ae68-1a42-4441-8102-f6eb4c3a7eab",
	"Data": [{
		"ELBHealthCheck": [{
			"Name": "ASG_dev_09_06_2017",
			"HealthCheckStatus": "Healthy",
			"HealthCheckDescription": "instance is registered"
		}],
		"IsHealthy": true,
		"ELBHealthCheckDetailsAsString": "Healthy - instance is registered behind jayaa_dev_09_06_2017",
		"InstanceId": "i-02b315e6afbe78876",
		"InstanceType": "t1.micro",
		"SubnetId": "subnet-aac48781",
		"AvailabilityZone": "us-east-1c",
		"LifeCycle": null,
		"Status": "running",
		"LaunchTime": "Friday 23 Jun 2017 05:50:15",
		"PrivateIpAddress": "172.31.49.28",
		"Name": null,
		"StopTime": null,
		"Distribution": "None"
	}],
	"Errors": {},
	"ContinuationToken": null
}

```
GET HTTP Method gets the run instance details 


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/runs/{Run ID}/summary"`</b>

### **Query Parameter**

Parameter |Data Type |Description
--------- | -------  |-------------
RunID |String|Job Run ID


<aside class=  "success">
Job run Instance details retreievd successfully 
</aside>

## Get Run Logs
>To get the Job run logs 

```shell

curl "http://<customer.cmpute.io>/api/v2/runs/{run ID}/logs"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell
{
	"Logs": [{
		"Message": "<string>",
		"Time": "<DateTime>",
		"Severity": "<string>"
	},  
	"RequestId": "02be44aa-91f4-48bf-90f1-552a43de1a52",
	"Errors": {}
}

```
>Example

```shell
{
	"Logs": [{
		"Message": "Maintaining Desired State",
		"Time": "Friday 23 Jun 2017 05:51:16",
		"Severity": "Info"
	}, {
		"Message": "Launching 1 t1.micro instances",
		"Time": "Friday 23 Jun 2017 05:50:12",
		"Severity": "Info"
	}, {
		"Message": "Run Started",
		"Time": "Friday 23 Jun 2017 05:48:55",
		"Severity": "Info"
	}],
	"RequestId": "02be44aa-91f4-48bf-90f1-552a43de1a52",
	"Errors": {}
}

```

GET HTTP Method gets the run logs  


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/runs/{run ID}/logs"`</b>

### **Query Parameter**

Parameter |Data Type |Description
--------- | -------  |-------------
RunID |String|Job Run ID


<aside class=  "success">
Job run logs retreievd successfully 
</aside>

## Get Right Size Recommendations
>To get Right Size recommendations for a Job

 ```shell

curl "http://<customer.cmpute.io>/api/v2/runs/R-AFD84C58/RightSizeRecommendations"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell

{
	"Recommendation": {
		"Recommendations": "<string>",
		"CurrentInstances": "<string>",
		"AverageCPUUtilization": float,
		"Message": "<strinmg>",
		"Available": boolean
	},
	"RequestId": "a1659a5c-bf76-41f6-93d1-e6e8139f3752",
	"Errors": {}
}

```
>Example

```shell
{
	"Recommendation": {
		"Recommendations": null,
		"CurrentInstances": null,
		"AverageCPUUtilization": 10.671,
		"Message": "No recommendation required",
		"Available": false
	},
	"RequestId": "a1659a5c-bf76-41f6-93d1-e6e8139f3752",
	"Errors": {}
}

```

GET HTTP Method gets the Right Size Recommendations for optimal usage of instances  


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/runs/R-AFD84C58/RightSizeRecommendations"`</b>

### **Query Parameter**

Parameter |Data Type |Description
--------- | -------  |-------------
RunID |String|Job Run ID


<aside class=  "success">
Instance Rightsize recommendations retreievd successfully 
</aside>



# AMI- Amazon Machine Images


## Create an AMI Job
>To create a new AMI Job

```shell

curl "http://<customer.cmpute.io>/api/v2/apps/Ami/Add"
  -H "Authorization: ApiKey AccessKey:SecretKey"

```
>The above command returns JSON structured like this:

```shell
{
	"Job": {
		"Runs": 0.0,
		"IsScheduled":boolean ,
		"IsExecuting": boolean,
		"Engine": "<string>",
		"AppName": "<string>",
		"IsPrivateApp": boolean,
		"Id": "<string>",
		"Name": "<string>"
	},
	"RequestId": "<string>",
	"Errors": {}
}

```
>Example

```shell
{
	"Job": {
		"Runs": 0.0,
		"IsScheduled": false,
		"IsExecuting": false,
		"Engine": "Cluster",
		"AppName": "AMI",
		"IsPrivateApp": false,
		"Id": "W-33xx0598",
		"Name": "AMI_JOB"
	},
	"RequestId": "970443xx-36a0-45f1-9730-934e0xx39244",
	"Errors": {}
}

```

POST HTTP Method creates a new AMI job   


**Note**
AMI app also supports Application load balancer. Elastic load balancer and Application load balancer can not be used together. 

For Example: If you are using Application load balancer, remove the Elastic load balancer from the JSON,

<font color= "Red">`"ElasticLoadBalancerNames": ["ELB-1", "ELB-2"]`</font>

and Application load balancer or vice-versa. 

<font color= "Red">`"TargetGroupARNs": ["ALB-1", "ALB-2"]`</font>


**HTTP Request**

<b>`Endpoint - <customer.cmpute.io>/api/v2/apps/Ami/Add"`</b>

### **Query Parameter**

Parameter |Data Type |Description
--------- | -------  |-------------
AccountId|String|(required)
Name||(required) Job Name
BaseRegion

InstanceProfileArn
ElasticLoadBalancerNames

SecurityGroupIds
SubnetIds
TargetGroupARNs ELB
VpcId

AMI ID|String|(required)
AssociatePublicIpAddress|
BaseRegion||
DesiredInstanceCount

HealthCheckGracePeriod
InstanceProfileArn
InstanceType
KeyPair
LaunchScript

MaxInstanceCount
MinInstanceCount
MinOnDemandInstanceCount
Name

ReplaceUnhealthyInstances
RestrictToSelectedInstance

EvaluationPeriods : 1
MetricStatisticType: "Average"
Period: 300
ScaleAt: 1
ScaleFactor: 1
ScaleType: "ScaleUp"
MetricName: "CPUUtilization"
Namespace: "AWS/EC2"
Unit: Seconds

EvaluationPeriods: 
MetricStatisticType: Average
Period: 300
ScaleAt: 1
ScaleFactor: 1
ScaleType: "ScaleDown
MetricName: "CPUUtilization"
Namespace: "AWS/EC2"
Unit: "Seconds"
    }




<aside class=  "success">
New AMI Job created successfully 
</aside>


