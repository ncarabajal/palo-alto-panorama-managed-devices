# palo-alto-panorama-managed-devices

Managed Device Summary Script
This Python script connects to multiple Panorama devices, retrieves information about the managed devices, and compiles the data into a CSV file. It prompts the user for a username and password at runtime to securely authenticate with the Panorama devices.

## Table of Contents
Prerequisites
Installation
Usage

## Prerequisites

Before running the script, ensure you have the following:

Python 3.x installed on your system.
Network Connectivity to the Panorama devices listed in the script.
Valid Credentials for the Panorama devices with the necessary permissions to retrieve device information.
Access Rights to install Python packages if they are not already installed.

## Installation

Follow these steps to set up the environment and run the script:

### 1. Clone the Repository
```
git clone https://github.com/ngacarabajal/palo-alto-panorama-managed-devices
cd managed-device-summary
```
### 2. (Optional) Create a Virtual Environment

It's recommended to use a virtual environment to manage dependencies:
```
python3 -m venv venv
source venv/bin/activate  # On Windows use 'venv\Scripts\activate'
```
### 3. Install Required Python Packages

The script requires the requests package. Install it using pip:
```
pip install requests
```
Note: The xml.etree.ElementTree, csv, and getpass modules are part of the Python Standard Library and do not require separate installation.

## Usage
### 1. Modify the Script
The script contains a dictionary named panoramas that lists the Panorama devices and corresponding output filenames:
```
panoramas = {
    'pano1-address': 'pano1_device_summary.csv',
    'pano2-address': 'pano2_device_summary.csv',
    'pano3-address': 'pano3_device_summary.csv',
}
```
### To Add or Remove Panorama Devices:
Add or remove entries in the panoramas dictionary as needed.
The key is the Panorama hostname or IP address.
The value is the desired output filename (not used in the combined output but can be modified for clarity).
### 2. Run the Script
Execute the script using Python:
```
python managed_device_summary.py
```
### 3. Enter Credentials
When prompted, enter your Panorama username and password:
```
Enter username: your_username
Enter password:
Username: Your Panorama username.
Password: Your Panorama password (input is hidden for security).
```
### 4. Wait for Completion
The script will:

Connect to each Panorama device listed.
Retrieve device information using the Panorama XML API.
Compile the data into a single CSV file named managed_device_summary.csv.

### 5. Review the Output
After the script completes:

Locate the managed_device_summary.csv file in the script directory.
Open the CSV file with a spreadsheet application or text editor to review the compiled device information.

It will output a csv with the following information:

        "Device Group", "Device Name", "Virtual System", "Model", "Tags", "Serial Number", 
        "IP Address IPv4", "IP Address IPv6", "HA HA Pair Status", "Variables", "Template", 
        "Status Device State", "Status Device Certificate", "Status Device Certificate Expiry Date", 
        "Status Shared Policy", "Status Template", "Status Certificate", 
        "Status High Speed Forwarding Mode", "Status Mode", "Status Shared Policy Last Commit State", 
        "Status Template Last Commit State", "Status Last Merged Diff", 
        "Software Version", "Apps And Threat", "Antivirus", "URL Filtering", 
        "GlobalProtect Client", "WildFire", "Device Dictionary", "Plugins", 
        "Last Master Key Push Status", "Last Master Key Push Timestamp"
