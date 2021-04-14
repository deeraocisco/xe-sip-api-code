# Getting Started with IOS-XE SLP REST APIs


Sample Python script written in Python 3.8.5. The script demonstrates the use of IOS-XE SLP REST APIs to automate SLP workflows.
Smart Licensing Using Policy (SLP) was introduced in Cisco IOS-XE Amsterdam 17.3.2.


For more information, see [About Smart Licensing Using Policy](ios-xe-smart-licensing-api/intro.md#about-smart-licensing-using-policy).

## Use Case Description

For information about each API that is demonstrated in this script, see [API Endpoint and Description](ios-xe-smart-licensing-api/about-the-apis/api-endpoint-and-description).

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

1. In the ```api_keys:``` section enter the username and password that you use to log in to the CSSM Web UI. 
	```
	api_keys:
    	client_id: not required
        client_secret: not required
  		username: username1_cssm 
  		password: password1_cssm
	```
    
    >**Note**: Entries for ```client_id``` and ```client_secret``` are not required, because this version of the script does not interact with CSSM directly See the [Restrictions and Limitations](xe-sip-api-code/readme.md#restrictions-and-limitations) section in this README.md file for details.

2. In the ```devices:``` section, enter access information for each one of your devices. The term "device" here refers to the product instance. 

	For ```id:``` provide a monotonically increasing ID.

	For ```ip:``` provide the management IP address

	For ```username:``` provide the username to log in to the device. 

	For ```password:``` provide the and the username to log in to the device. 

	```
    devices:
  
    	id: 1
    	ip: 175.25.212.187
    	username: username2
    	password: password2
	```


## Usage

Run the Python script in a command line interface (CLI) by entering the Python command. 

```
python sl-api-demo.py
``` 

Running the script provides you with four operations to choose from:
1. Get a list of Smart Accounts and Virtual Accounts associated with the CSSM username.
   >**Note**: This option is not an API on the device.  The sample code furnished here, provides this additional option. 
2. Collect RUM reports for all the product instances listed in the config.yaml file for the default duration of 90 days.
   
   Selecting this option also automatically closes all _open_ RUM reports on the product instance.
   
   After you have collected the RUM reports, manually upload the RUM reports to the corresponding Smart Account and Virtual Account in CSSM and then download the ACK.

3. Send a RUM ACK file to all the product instances listed in the config.yaml file. The script performs this action, one product instance at a time. 
4. Sends the custom policy file to all product instance listed  in the config.yaml file

```
    print("  (1) Online CSSM: API to get list of SA/VA")
    print("  (2) Offline CSSM: Collect RUM reports using IOS-XE API and upload offline")
    print("  (3) Offline CSSM: Apply RUM ACK using IOS-XE API (One device at a time)")
    print("  (4) Offline CSSM: Apply custom-policy to all devices")
```

## Restrictions and Limitations

* This version of the script does not interact with CSSM directly. (CSSM APIs are available for use;  its only this sample code that does not support it).

	_When using this script_, note that all CSSM operations (communication between your own Smart Licensing application and CSSM),  must be performed manually by logging in to the CSSM Web UI at https://software.cisco.com,  and then uploading or downloading the necessary files.
    

* An API to _delete_ a RUM report is not supported. This is because RUM reports, once closed, are immutable. To erase all data from a product instance, see [Decommissioning a Product Instance](ios-xe-smart-licensing-api/workflows.md#decommissioning-a-product-instance).

* An API to return a SLAC (for export-controlled or enforced licenses or throughput greater than 205 Mbps) is currently not supported.


## Getting Help

If you have questions, concerns, bug reports, etc., please create an issue against this repository.

## Getting Involved

To provide feedback about IOS-XE SLP REST APIs,  see [CONTRIBUTING](./CONTRIBUTING.md).

## Licensing info

This code is licensed under the Cisco sample code license. For details, see [LICENSE](LICENSE.md).
