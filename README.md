# Getting Started with Cisco IOS-XE Smart licensing APIs

Sample code in Python that shows how to call IOS-XE SLP REST APIs. You can automate the usage reporting workflows using these APIs.

For information about Smart Licensing Using Policy (SLP), see [About Smart Licensing Using Policy](ios-xe-smart-licensing-api/intro.md#about-smart-licensing-using-policy).

## Use Case Description

For information about the purpose of each currently available API, see [About IOS-XE SLP REST APIs](ios-xe-smart-licensing-api/intro.md#about-ios-xe-slp-rest-apis).

Future enhancements include an API to return a Smart Licensing Authorization Code (SLAC).

## Installation

Python must be installed. Further the following Python packages are required:
* os
* shutil
* json
* xmltodict
* requests
* yaml
* tarfile

## Configuration
Configure the following where? we have to check CSSM API docs to know this and then add. 

client_id: 55f65e59-df52-4073-bb12-4268d5167019 (the user has to enter their own;  will enquire how this should be done)
client_secret: 78962244-9f2f-4e50-b233-f92adedd1e33 (the user has to enter their own; will enquire how this should be done)
username: CSSM log in username (update config.yaml with dummy username)
password: CSSM log in password (update config.yaml with dummy password)


## Usage

-tbd-


## How to Test the Software

-tbd-
This may not be applicable. 

## Restrictions and Limitations

* An API to _delete_ a RUM report is not supported. This is because RUM reports, once closed, are immutable. To erase all data from a product instance, see [Decommissioning a Product Instance](ios-xe-smart-licensing-api/workflows.md#decommissioning-a-product-instance).

* An API to return a SLAC (for export-controlled or enforced licenses or throughput greater than 205 Mbps) is currently not supported.


## Getting Involved

<check with Ryan about standard protocol -  can we create an alias and provide it here? >

## Licensing info

This code is licensed under the Cisco sample code license. See [LICENSE](LICENSE.md) for details.
