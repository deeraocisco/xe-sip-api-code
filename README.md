# Getting Started with IOS-XE SLP REST APIs


Sample Python script written in Python 3.8.5. The script demonstrates the use of IOS-XE SLP REST APIs to automate Smart Licensing Using Policy (SLP) workflows.

SLP was first introduced on Cisco IOS-XE product instances in release Cisco IOS-XE Amsterdam 17.3.2. For more information, see [About Smart Licensing Using Policy](https://developer.cisco.com/docs/ios-xe/smart-licensing/#!introduction/about-smart-licensing-using-policy).

## Use Case Description

For information about each API that is demonstrated in this script, see [API Endpoint and Description](https://developer.cisco.com/docs/ios-xe/smart-licensing/#!about-the-apis/api-endpoint-and-description).

Future enhancements include an API to return a Smart Licensing Authorization Code (SLAC).

## Installation

Install [Python](https://www.python.org/downloads/) and the required packages. 

* Python version: 3.8.5
* Required Python packages:
  * os
  * shutil
  * json
  * xmltodict
  * requests
  * yaml
  * tarfile
  

## Configuration


Configure the following in the ```config.yaml``` file: 

1. Turn-on the connection to CSSM.
	```
	cssm_connection: on
	```
2. Enter the ```client_id:``` and ```client_secret```. 

	```
    api_keys:
  
    client_id: <Your client_id obtained from apidocs-prod.cisco.com>
	
	client_secret: <Your client_secret obtained from apidocs-prod.cisco.com>
	```
For information about generating a Client ID and a Client Secret,  see https://apidocs-prod.cisco.com/?path=requestapiinfo.  

3. Enter access information for each one of your product instances.  

	```
    devices:
  
    	id: 1
    	ip: 175.25.212.187
    	username: username2
    	password: password2
	```
	For ```id:``` provide a monotonically increasing ID.

	For ```ip:``` enter the management IP address of the product instance.

	For ```username:``` provide the username to log in to the product instance. 

	For ```password:``` provide the and the username to log in to the product instance. 

## Usage

Run the Python script by entering the **python** command in a command prompt or shell prompt. 

```
python sl-api-demo.py
``` 

Running the script provides you with four operations to choose from:
```
    print("  (1) Online CSSM: API to get list of SA/VA")
    print("  (2) Offline CSSM: Collect RUM reports using IOS-XE API and upload offline")
    print("  (3) Offline CSSM: Apply RUM ACK using IOS-XE API (One device at a time)")
    print("  (4) Offline CSSM: Apply custom-policy to all devices")
```
1. "  (1) Online CSSM: API to get list of SA/VA": This option gets a list of Smart Accounts and Virtual Accounts associated with the CSSM username.
   >**Note**: This option is not an API on the product instance.  The sample code furnished here, provides this additional option. 

2. "  (2) Offline CSSM: Collect RUM reports using IOS-XE API and upload offline":  This option collects RUM reports for all the product instances listed in the config.yaml file for the default duration of 90 days.
   
   Selecting this option also automatically closes all _open_ RUM reports on the product instance.
   
   After you have collected the RUM reports, manually upload the RUM reports to the corresponding Smart Account and Virtual Account in CSSM and then download the ACK.

3. "  (3) Offline CSSM: Apply RUM ACK using IOS-XE API (One device at a time)": This option sends a RUM ACK file to all the product instances listed in the config.yaml file. The script performs this action, one product instance at a time. 
4. "  (4) Offline CSSM: Apply custom-policy to all devices": This options sends the custom policy file to all product instance listed  in the config.yaml file.



## Restrictions and Limitations

* This version of the script does not interact with CSSM directly. (CSSM APIs are available for use;  its only this sample code that does not support it).

	_When using this script_, note that all CSSM operations (communication between your own Smart Licensing application and CSSM),  must be performed manually by logging in to the CSSM Web UI at https://software.cisco.com,  and then uploading or downloading the necessary files.
    

* An API to _delete_ a RUM report is not supported. This is because RUM reports, once closed, are immutable. To erase all data from a product instance, see [Decommissioning a Product Instance](https://developer.cisco.com/docs/ios-xe/smart-licensing/#!recommended-workflows/decommissioning-a-product-instance).

* An API to return a SLAC (for export-controlled or enforced licenses or throughput greater than 250 Mbps) is currently not supported.


## Getting Help

If you have questions, concerns, bug reports, etc., please create an issue against this repository.

## Getting Involved

To provide feedback about IOS-XE SLP REST APIs,  see [CONTRIBUTING](./CONTRIBUTING.md).

## Licensing Information

This code is licensed under the Cisco sample code license. For details, see [LICENSE](LICENSE.md).
