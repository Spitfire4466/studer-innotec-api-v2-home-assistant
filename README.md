# Getting Studer-Innotec API v2 data to Home Assistant via Node-Red
This short guide explains how to get data from the Studer-Innotec API V2 to Home Assistant using Node-Red

### References
https://studer-innotec.com/fr/  
https://api2.studer-innotec.com/swagger/  

# Requirements
- A working installation of Home Assistant  
- Node-RED App installed and running  
- Node-RED Companion Integration: https://github.com/zachowj/hass-node-red  
- A working Studer-Innotec installation connected to their portal: https://portal.studer-innotec.com/  
- Studer-Innotec login credentials obviously  
- Your installation Id (a set of numbers) which you can find here: https://portal.studer-innotec.com/Installation  

# How to

## Step 1 helpers
Create two helpers in Home Assistant:
- Input Text helper named: ***Studer_token***
- Input Text helper named: ***Studer_Refresh_token***
- To create helpers go to Settings -> Device and services -> helpers -> create helper -> text

## Step 2 import
- Import the Node-Red flow from the file: [***studer-innotec-api-v2-access-node-red.json***](studer-innotec-api-v2-access-node-red.json)  
- To import go to Node-Red, then the top right menu -> import and paste the code or directly upload the .json file  
- It will create a new ***Studer V2 Get Data*** tab and you should have a structure that looks like the image below  
- Do not deploy yet as some edits are required for things to work
<img width="1532" height="1460" alt="structure" src="https://github.com/user-attachments/assets/86fa0c31-c2b1-4701-8e35-2ff5cca75482" />


## Step 3 credentials
Edit the first node named ***Request Token with Password*** and add your username and password in the correct fields

## Step 4 Installation Id
Open the settings for the node named ***get DATA http request*** and edit the url by replacing the set of number with your installation Id
<img width="2170" height="1838" alt="api-request-install-number" src="https://github.com/user-attachments/assets/89b80cb3-591b-4cd9-80d2-3410cb7edd9e" />


## Step 5 sensors
You will most likely have to manually create the sensors for your Home Assistant instance as these cannot be imported.
  
See image below how to create the first sensor via Node-Red companion for ***Studer V2 Solar Power W sensor***.      
name: Studer V2 Solar Power W  
type: sensor  
Friendly name: Studer V2 Solar Power W  
Device class: Power  
Unit of measurement: W  
state class: measurement  
  
<img width="6586" height="3406" alt="studer-v2-access-node-red" src="https://github.com/user-attachments/assets/9915721b-e54a-47b9-84d7-4e6cd344e905" />

### Repeat this operation for all sensors following this list:

name: Studer V2 Solar Power kW  
type: sensor  
Friendly name: Studer V2 Solar Power kW  
Device class: Power  
Unit of measurement: kW  
state class: measurement  
  
name: Studer V2 Solar Production kWh  
type: sensor  
Friendly name: Studer V2 Solar Power kW  
Device class: energy  
Unit of measurement: kWh  
state class: total increasing  
  
name: Studer V2 Grid Consumed kWh  
type: sensor  
Friendly name: Studer V2 Grid Consumed kWh  
Device class: energy  
Unit of measurement: kWh  
state class: total increasing  
  
name: Studer V2 Battery Charge kWh  
type: sensor  
Friendly name: Studer V2 Battery Charge kWh  
Device class: energy  
Unit of measurement: kWh  
state class: total increasing  
  
name: Studer V2 Battery Discharge kWh  
type: sensor  
Friendly name: Studer V2 Battery Discharge kWh  
Device class: energy  
Unit of measurement: kWh  
state class: total increasing  
  
name: Studer V2 Battery In W  
type: sensor  
Friendly name: Studer V2 Battery In W  
Device class: power  
Unit of measurement: W  
state class: measurement  
  
name: Studer V2 Battery Out W  
type: sensor  
Friendly name: Studer V2 Battery Out W  
Device class: power  
Unit of measurement: W  
state class: measurement  
  
name: Studer V2 Battery Power in-Out kW  
type: sensor  
Friendly name: Studer V2 Battery Power in-Out kW  
Device class: power  
Unit of measurement: kW  
state class: measurement  
  
name: Studer V2 Battery Power in-Out W  
type: sensor  
Friendly name: Studer V2 Battery Power in-Out W  
Device class: power  
Unit of measurement: W  
state class: measurement  
  
name: Studer V2 Battery SOC  
type: sensor  
Friendly name: Studer V2 Battery SOC  
Device class:   
Unit of measurement: %  
state class:   

name: Studer V2 House Consumption  
type: sensor  
Friendly name: Studer V2 House Consumption  
Device class: power  
Unit of measurement: kW  
state class: measurement  

## Step 6 Deploy, test and adapt
- Try to deploy the modified nodes, trigger manually if need be and look at the debug panel for any errors
- All created sensors will appear in the Entities list of Home Assistant, search for ***studer v2***
- Now you can edit to your liking. To access the list of available data, connect the ***Get the structure and display in debug window*** Node and redeploy. An object will appear in your debug window containing all the available data from the synoptic request for API v2, look through it and ignore the error message.
