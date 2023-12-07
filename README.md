<div align="center">
    <img src="Processes/Process%202%20(images)/PRO.png" alt="My Image" width="350" height="350">
</div>

## <div align="center"> Master of Science in Medical Informatics: Digitization of Business Processes in Healthcare (Autumn-2023) </div>

**Team Name**: Victorinox

**Topic**: Digital Pharmacy

**Product Name**: PRO Pharmacy

**Deliverables**: 
1) GitHub repositories with modeling and technical artefacts as well as the supporting documentation.
2) Links to a running workflows and microservice instantiations.
3) A PowerPoint presentation.

**Presentation Date**: December 7th, 2023

#### Members:

| **Names**         | **Emails**                          |
|-------------------|-------------------------------------|
| Alberto Wicker    | alberto.wickervera@students.fhnw.ch |
| John Arellano     | john.arellano@students.fhnw.ch      |
| Dominic Richner   | dominic.richner@students.fhnw.ch    |

## <div align="center"> Introduction </div>

**Patient Reported Outcome (PRO)** measures include any health outcome evaluated directly by the patient themselves and are based upon the patient’s perception of a disease as well as its treatment. It is an umbrella term that covers measures of symptoms, health status, adherence to treatment, satisfaction with treatment, and Health-Related Quality of Life (HRQL), among others. **Health-Related Quality of Life (HRQL)** is a specific type of PRO that can best be understood as the patient’s subjective perception of how a disease and its treatment impacts their daily life. These aspects of health, directly reported by patients, cover areas that conventional clinical measures often fail to capture like psychological well-being and social functioning. 

The data gathered from this type of patient-centric perspective on the advantages and disadvantages of taking a particular medication empowers health professionals to improve our understanding of what outcomes from a treatment matter most to patients. For this reason, the Victorinox team has collaborated to seamlessly incorporate a program called ePRO into our digital pharmacy's business model that administers HRQL surveys to patient's who've been prescribed a drug in Phase IV clinical trials with marketing approval. By collecting, contextualizing, and sharing this data with health professionals, we hope to improve the medical community's understanding of how particular drugs impact the quality of life of patients and, in turn, make a meaningful impact on improving patient HRQL.

## <div align="center"> Goals </div>

Victorinox’s objective was to seamlessly integrate a PRO program (ePRO) into the business model of our digital pharmacy that would collect HRQL data from patients who have been prescribed a drug in Phase IV clinical trials with marketing approval. This required innovation in three 3 key areas of our existing model:

- **Prescription Handling:** Prescription authentication and enrollment into ePRO is managed by the patient's physician. This process required the automation of ePrescription email notifications being sent to inform all parties (e.g., the patient, prescribing physician, and pharmacy) of prescription authentication upon submission of the ePrescription form. The patient data from this form is collected in our database (an ePrescription response Google form).
- **HRQL Instrument:** Patients who have been prescribed a drug in Phase IV clinical trials and been enrolled into ePRO, receive an email that is periodically sent  requesting them to fill out the HQLR questionnaire.
- **Data Analysis and Reporting:** Data from the ePrescription database and ePRO databases (containing the patient responses to the HQLR questionnaire) are automatically pulled from to generate a weekly report which is subsequently shared with our partners.

For this project, we've chosen to focus on HRQL measures for drugs in Phase IV (post-marketing) clinical trials to monitor long-term impacts on patient quality of life in a real-world setting. The HRQL measure that we designed as an example is exclusively for patients diagnosed with chronic migraines (encompassed in ICD-10: G43) and is based on the "Migraine Specific Quality of Life" (MSQOL). The insights gained from these reports can aid pharmaceutical companies in tailoring their products to meet previously unidentified patient needs, re-defining their market strategies, distinguishing their drugs from competitors, and potentially influencing the design of future clinical trials.

## <div align="center"> Final BPMN & Workflow </div>

<div align="center">
    <img src="Processes/To-be%20Processes/PRO_pharmacy_V4(final).png" alt="Readme Files" style="width: 70%;">
</div>
  

<div align="center">
    <img src="Processes/Process%202%20(images)/PRO%20Pharmacy%20Workflow.png" alt="Readme Files" style="width: 70%;">
</div>

## <div align="center"> Main Elements </div>

#### <div align="center"> Google Forms </div>

**Prescription and PRO-Enrollment Form**: This Google form is filled by the patient's prescribing physician and is the point at which a patient that has been prescribed a drug in Phase IV clinical trials would be enrolled into the PRO Quality of Life (ePRO) program. In this prototype of our model, we deal exclusively with patients who have  been prescribed a drug for chronic migraines.  

- link: https://docs.google.com/forms/d/e/1FAIpQLSfWLpVzlgVTRrDKF1wfn1xS9ThDHiE4BDS-moLOmF4V7PPMuA/viewform?usp=sharing

**Quality of Life ePRO (Questionnaire) Form**: This Google form is filled by the patient on a monthly basis. In future iterations of the program, we would generate a questionnaire that applies to every type of medical condition that could conceivably be treated by a drug in Phase IV clinical trials. This particular iteration of the PRO-form is based on the recommendations found in the European Medical Agency's (EMA) regulatory guidance for the use of health-related quality of life (HRQL) measures in the evaluation of medicinal products and the Migraine-Specific Quality-of-Life Instrument (MSQOL) - a measure designed to assess the quality of life of migraineurs.

- link: https://docs.google.com/forms/d/e/1FAIpQLSc2L2cH2rir96DBVvtVYWALDP-yHIFVZDvBC6I0d1iZ9hOw4g/viewform?usp=sharing

#### <div align="center"> Google Sheets </div>

**Prescription and PRO-Enrollment Responses**: This Google sheet contains all of the responses from the physicians who filled out the Prescription and PRO-Enrollment Form.

- link: https://docs.google.com/spreadsheets/d/1ypOGj5-N9hIeWRvFA12JYLfqmpYX-8iFOVw-5kGGtyc/edit?usp=sharing

**Quality of Life ePRO (Questionnaire) Responses**: This Google sheet contains all of the patient responses to the Quality of Life PRO-Questionnaire form for migraines.

- link: https://docs.google.com/spreadsheets/d/1qe99zlcNP3slzNdWAdgirf_a88HzSm3_D2ZbBBWLPSc/edit?usp=sharing

#### <div align="center"> Apps Scripts </div>

**ePrescription** (Doc, QR, Emails)
**Triggered by form submissions**: Creates a Google Doc for each ePrescription Form submission, it includes relevant details for the patient's prescription. The document is shared via a URL that generates a QR code. This QR code contains the prescription Document, and is emailed to the patient, physician, and a PRO Pharmacy. Finally, the QR code is inserted into the ePrescription Form (Responses) Sheet for record-keeping. The final step is a cleanup process where the prescription document is sent to the trash and expires on 30 days.
- link: https://script.google.com/u/0/home/projects/1VzjttMBquePwKhkX1ZhEvc_Y6TTLFy3YXdQ3eRqG2LVxo7UGkxsF99BK/edit

**ePRO** (colab VIZ script)
**Triggered by form submissions**: Adds longitude and latitude to column 14 and 15 of the ePRO (Response) Sheet, respectively. For each form submission, it combines street, zip, and city information to obtain latitude and longitude, which are then added to the columns in the sheet. The script manages addresses in Switzerland and handles errors when the script does not return a result.
- link: https://script.google.com/u/0/home/projects/1YEapO_Fc2_eZS1A2NrFAhlawmzkorGyFHZmKq-hdlaPc2TExKN3PMHVY/edit

## <div align="center"> Process 1 (in-depth): Prescription Verification & PRO Enrollment </div>

Process one begins with a google form, which is filled out by the physician with information on the doctor, patient, perscription, and PRO enrollment status. Furthermore, a QR Code is generated and sent via email to the patient if they are enrolled into ePRO in order to complete the HRQL questionnaire. 

<div align="center">
    <img src="Processes/Process%201%20(images)/P1_Prescription%20Verification.jpg" alt="P1 Prescription Verification" style="width: 70%;">
</div>

**Make Scenario 1**: [blueprint Integration Google Sheets, HTTP request.json](Processes/blueprint%20Integration%20Google%20Sheets%2C%20HTTP%20request.json)

In the make scenario, the Google sheet ePrescription Form (Responses) is watched for the addition of new rows. When they appear, a request via the HTTP POST method is made with a json request content (): 

{
"variables":{

"timestamp":{
"value":"{{4.`0`}}",
"type":"String"},

"doctorEmail":{
"value":"{{4.`1`}}",
"type":"String"},

"medLicenseNr":{
"value":"{{4.`3`}}",
"type":"String"},

"physician":{
"value":"{{4.`2`}}",
"type":"String"},

"patientName":{
"value":"{{4.`4`}}",
"type":"String"},

"dateOfBirth":{
"value":"{{4.`5`}}",
"type":"String"},

"healthInsuranceDetails":{
"value":"{{4.`6`}}",
"type":"String"},

"dateOfPrescription":{
"value":"{{4.`7`}}",
"type":"String"},

"medicationPrescribed":{
"value":"{{4.`8`}}",
"type":"String"},

"quantityToDispense":{
"value":"{{4.`9`}}",
"type":"String"},

"directionsForUse":{
"value":"{{4.`10`}}",
"type":"String"},

"diagnosisICD10":{
"value":"{{4.`11`}}",
"type":"String"},

"descriptionOfDiagnosis":{
"value":"{{4.`12`}}",
"type":"String"},

"allergiesAndMedInteractions":{
"value":"{{4.`13`}}",
"type":"String"},

"patientEmail":{
"value":"{{4.`14`}}",
"type":"String"},

"enrollment":{
"value":"{{4.`15`}}",
"type":"String"}


}
}

<div align="center">
    <img src="Processes/Process%201%20(images)/PRO_pharmacy_V3_P1(2).png" alt="PRO Pharmacy V3 P1" style="width: 70%;">
</div>

In camunda the form ids are defined and used in the aforementioned json and the corresponding value is selected in make. The gate checks the condition verify equals true or false, which is processed by a user task and is followed by the user task "dispense medication".

<div align="center">
    <img src="Processes/Process%201%20(images)/P1-webhook-Dispense-Confirmation.jpg" alt="P1 Webhook Dispense Confirmation" style="width: 70%;">
</div>

**Make Scenario 2**: [blueprint-Webhook.json](Processes/blueprint-Webhook.json)

The make scenario with the webhook and send email modules are scheduled for submission as soon as data arrives and therefore does not need to be run immediately. A medication dispensation email will be sent from teamvictorinoxoutlook.com account with the following text:
<<Dear Customer, the medication you orderd has been dispensed. Thank you for choosing our pharmacy. Your Victorinox team.
>>

An email is sent to patient's enrolled into ePRO containing a link to the form. The router determines which service task is being called and routes to the corresponding email sending module.

1. Deploy the camunda model.
2. The physician fills out the patient form.
3. Run Scenario 1: google sheets -> HTTP POST method API call sends a json object to camunda.

The following are done automatically in the camunda cockpit:
   
   a) Task list opened

   b) Start process button clicked

   c) process to be started chosen

   d) process started

   

The form then needs to be claimed and the verify check box needs to be selected by the pharmacy employee manually.

## <div align="center"> Process 2 (in-depth): Analysis & Report Generation </div>

<div align="center">
    <img src="Processes/Process%202%20(images)/P2_BPMN.png" alt="P2 BPMN" style="width: 70%;">
</div>

## <div align="center"> ## First Element: Timer Start Event (Weekly Report) </div>
The process begins with a Timer Start Event set in the BPMN diagram (Camunda Platform 7). This timer, configured as a "Cycle" type, initiates the process every 10 seconds for demonstration. This process will run automatically each each, generating a new report every Monday morning.

<div align="center">
    <img src="Processes/Process%202%20(images)/P2_timer_start_event.png" alt="P2 Timer Start Event" style="width: 20%;">
</div>

## <div align="center"> Second Element: Service Task (Generate and send report to senior) </div>
The primary objective of this task is to generate a PDF report, which is then sent to our partners via email. It involves two connector inputs: 
1. An input with an assignment type of "String or Expression" and a value of GET.
2. An input (also a "String or Expression") containing the tunneling link for our PRO Pharmacy REST API (Python Flask) developed in Deepnote.

<div align="center">
    <img src="Processes/Process%202%20(images)/P2_generate_report.png" alt="P2 Generate Report" style="width: 20%;">
</div>

## <div align="center"> PRO Pharmacy REST API (Python Flask) </div>

<div align="center">
    <img src="Processes/Process%202%20(images)/deepnote.png" alt="Deepnote" style="width: 40%;">
</div>

The REST API developed in Deepnote's Python environment is designed to analyze the ePrescription and ePRO data from the Google Sheets. 

**Key Features:**

- **Flask Web Application Setup**: A Flask app is established to serve as the interface of the system.
- **Data Loading from Google Sheets**: The code accesses our databases (ePrescription and ePRO Responses) using Gspread and OAuth2Client with a JSON file (API key credential) generated in Google Cloud Platform.
- **Data Analysis**: This involves creating visualizations, which are then saved as PNG files. These visualizations include Daily Prescriptions (line plot), Prescriptions per Medication (horizontal bar chart), Age Distribution of Patients (histogram), Improvements in Migraines (histogram), and Geographical Distribution (horizontal bar chart) and a map of Switzerland (using longitude and latitude from the ePRO Responses dataset and .shp/.shx  images downloaded from DIVA-GIS https://diva-gis.org/gdata).
- **Report Generation using FPDF**: All saved PNG visualizations are compiled into a PDF. The title of the report is customized using datetime, and graphs are displayed over two pages.
- **Email Functionality with SendGrid (Cloud-Based Email Service)**: An API key is generated using SendGrid, enabling the sending of personalized emails with the attached PDF report for review by a senior at PRO Pharmacy before forwarding to our partners.

**The notebook is configured to run as a server using Flask, making the application accessible over the web.**

**Notebook Access**: [Flask.ipynb](REST%20API%20(Python%20Flask)/PRO%20(Flask).ipynb)

## <div align="center"> Third Element: User Task (Report validation by senior) </div>
This step is designated as a User Task because it requires a review by a senior member at PRO Pharmacy. The email generated in the previous Service Task, with the attached PDF report, is reviewed by a senior member who may add additional remarks before dispatching it to our partners.

<div align="center">
    <img src="Processes/Process%202%20(images)/P2_validate_report.png" alt="P2 Validate Report" style="width: 20%;">
</div>

<div align="center">
    <img src="Processes/Process%202%20(images)/P2_mail.png" alt="P2 Mail" style="width: 80%;">
</div>

## <div align="center"> Fourth Element: End Event </div>

The process concludes with the sending of the email to our pharmaceutical partners, marking the end of the second process.

<div align="center">
    <img src="Processes/Process%202%20(images)/P2_send_report.png" alt="P2 Send Report" style="width: 20%;">
</div>

## <div align="center"> Strategic Enhancement Opportunities </div>

**Develop a Web Service**: Implement a service for viewing prescriptions and reports to enhance credibility and user access.

**Integrate eSignature**: Incorporate a nationally trusted eSignature service within the ePrescription form to ensure security and authenticity.

**Expand HRQL Tool Variety**: Include validated and comprehensive forms tailored to multiple diseases. Streamline workflow to categorize each pathology into specific groups for more efficient 

**Implement Data Visualization Tools**: Utilize interactive platforms such as Tableau or Power BI for displaying reports, enabling more engaging and insightful data visualization. 

**Enhance Cybersecurity**: Elevate cybersecurity measures to protect sensitive data and maintain user trust.


## <div align="center"> References (APA-7): </div>

European Medicines Agency. (2005, July 27). *Regulatory guidance for the use of health-related quality of life (HRQL) measures in the evaluation of medicinal products - Scientific guideline*. https://www.ema.europa.eu/en/regulatory-guidance-use-health-related-quality-life-hrql-measures-evaluation-medicinal-products-scientific-guideline. https://www.ema.europa.eu/en/regulatory-guidance-use-health-related-quality-life-hrql-measures-evaluation-medicinal-products-scientific-guideline 

McKenna, S. P., Doward, L. C., &amp; Davey, K. M. (1998). The development and psychometric properties of the MSQOL. *Clinical Drug Investigation, 15*(5), 413–423. https://doi.org/10.2165/00044011-199815050-00006 

## <div align="center"> Acknowledgments </div>

A special thanks to Charuta Pande for her invaluable guidance and patience throughout this project. Her expertise was crucial in successfully manifesting and shaping our project vision.

We also extend our gratitude to Andreas Martin for providing us with the essential tools necessary to advance our project. His support played a significant role in our progress and success.
