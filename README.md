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

In camund the form ids are defined and used in the aforementioned json. The gate checks the condition verfy equals true or false (done with a user task).


