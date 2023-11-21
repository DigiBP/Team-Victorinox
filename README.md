<img src="PRO.png" alt="My Image" width="200" height="200">

# Team-Victorinox

# Members

Alberto Wicker
John Arellano
Dominic

# Introduction

Create an innovaitve digital pharmacy in the Swiss market.

# Goal

Our goal is to record PRO and identify unmet medical needs and record adverse drug effects in the post marekt stage of drugs.

# Process

The process starts with the doctor google form. 

<img src="makeScenario.png" alt="My Image" width="300" height="200">

In the make scenario the google sheet ePrescription Form (Responses) is watched for new rows. Furthermore a request via the HTTP POST method is made with a json request content: 

{      "variables": 
{        
"timestamp" : {          "value" : "{{1.`0`}}",          "type": "String"        },  
"doctorEmail" : {          "value" : "{{1.`1`}}",          "type": "String"        },   
"medLicenseNr" : {          "value" : "{{1.`3`}}",          "type": "String"        },   
 "physician" : {          "value" : "{{1.`2`}}",          "type": "String"        },        
"patientName" : {          "value" : "{{1.`4`}}",          "type": "String"        },  
 "dateOfBirth" : {          "value" : "{{1.`5`}}",          "type": "String"        },
"healthInsuranceDetails" : {          "value" : "{{1.`6`}}",          "type": "String"        }, 
"dateOfPrescription" : {          "value" : "{{1.`7`}}",          "type": "String"        }, 
"medicationPrescribed" : {          "value" : "{{1.`8`}}",          "type": "String"        }, 

"quantityToDispense" : {          "value" : "{{1.`9`}}",          "type": "String"        }, 
"directionsForUse" : {          "value" : "{{1.`10`}}",          "type": "String"        }, 
"diagnosisICD10" : {          "value" : "{{1.`11`}}",          "type": "String"        }, 
"descriptionOfDiagnosis" : {          "value" : "{{1.`12`}}",          "type": "String"        }, 
"allergiesAndMedInteractions" : {          "value" : "{{1.`13`}}",          "type": "String"        }, 
"patientEmail" : {          "value" : "{{1.`14`}}",          "type": "String"        }, 
"enrollment" : {          "value" : "{{1.`15`}}",          "type": "String"        }
 }   
 }

<img src="process one.png" alt="My Image" width="300" height="200">

