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

The process starts with a google form which is filled out by the doctore with information on the doctor, patient, the perscription and PRO and furthermore a QR Code is generated and sent via email. 

<img src="makeScenario.png" alt="My Image" width="300" height="200">

In the make scenario the google sheet ePrescription Form (Responses) is watched for new rows. Furthermore a request via the HTTP POST method is made with a json request content (): 

{      "variables": 
 {        
"timestamp" : {          "value" : "",          "type": "String"        },  
"doctorEmail" : {          "value" : "",          "type": "String"        },   
"medLicenseNr" : {          "value" : "",          "type": "String"        },   
 "physician" : {          "value" : "",          "type": "String"        },        
"patientName" : {          "value" : "",          "type": "String"        },  
 "dateOfBirth" : {          "value" : "",          "type": "String"        },
"healthInsuranceDetails" : {          "value" : "",          "type": "String"        }, 
"dateOfPrescription" : {          "value" : "",          "type": "String"        }, 
"medicationPrescribed" : {          "value" : "",          "type": "String"        }, 
"quantityToDispense" : {          "value" : "",          "type": "String"        }, 
"directionsForUse" : {          "value" : "",          "type": "String"        }, 
"diagnosisICD10" : {          "value" : "",          "type": "String"        }, 
"descriptionOfDiagnosis" : {          "value" : "",          "type": "String"        }, 
"allergiesAndMedInteractions" : {          "value" : "",          "type": "String"        }, 
"patientEmail" : {          "value" : "",          "type": "String"        }, 
"enrollment" : {          "value" : "",          "type": "String"        }
  }   
 }

<img src="process one.png" alt="My Image" width="900" height="300">

In camunda the form ids are defined and used in the aforementioned json and the corresponding value is selected in make. The gate checks the condition verfy equals true or false, this is processed by a user task and is followed by the user taks dispense medication.

