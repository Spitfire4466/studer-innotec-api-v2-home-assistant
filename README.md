# studer-innotec-api-v2-home-assistant
How to get data from Studer-Innotec API V2 to Home Assistant using Node-Red

# Requirements:
A working installation of Home Assistant
Node-RED App installed and running
Node-RED Companion Integration: https://github.com/zachowj/hass-node-red
A working Studer-Innotec installation connected to their portal: https://portal.studer-innotec.com/
Studer-Innotec login credentials obviously
Your installation Id (a set of numbers) which you can find here: https://portal.studer-innotec.com/Installation

# How to

## Step 1 helpers
Create two helpers:
- Input Text helper named: Studer_token
- Input Text helper named: Studer_Refresh_token
  To create helpers go to Settings -> Device and services -> helpers -> create helper -> text

## Step 2 import
Import the Node-Red flow from the file: studer-innotec-api-v2-access-node-red.json
To import go to Node-Red, then the top right menu -> import and paste the code or upload the .json file
You should now have a structure that looks like the image below
Do not deploy yet as some edits are required

## Step 3 credentials
Edit the first node named "Request Token with Password" and add your username and password in the correct fields

## Step 4 Installation Id
Open the settings for the node named "get DATA http request" and edit the url by replacing the set of number with your installation Id

## Step 5 sensors
You will most likely have to manually create the sensors for your Home Assistant instance.

List of sensor to create via Node-Red:

name: Studer V2 Solar Power W
type: sensor
Friendly name: Studer V2 Solar Power W
Device class: Power
Unit of measurement: W
state class: measurement

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
