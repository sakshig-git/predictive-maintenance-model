🚀 Predictive Maintenance Matrix(AI Powered Failure Prediction System)
 
"We don’t wait for failures. We predict them. We prevent them. We power the future." ⚙️📊
👥 Team Details
Team Name: Predictive Maintenance Matrix
Members:
Member 1 : Sandeep P
Member 2 : Sakshi Rajesh Gajghate
Member 3 : Joshi Bhargav Ammavajhala
Member 4 : Ramanjaneyulu Kurma
Member 5 : Yogitha Chundu
 
 
Domain Category: AI / Predictive Analytics / Industrial AI
Demo Video: Sharepoint URL of your MVP demo
 
🎯 Problem Statement
Industrial assets generate daily operational readings. However:
 
Data remains siloed
Failures are detected only after breakdown
Work orders are manually triggered
Field service response is delayed
 
Organizations need an automated, AI-driven failure prediction system that:
Integrates across enterprise platforms
Predicts failure probability
Automatically initiates service workflows
 
 
💡 Solution Overview
Predictive Maintenance Matrix is an enterprise-grade predictive maintenance solution that integrates:
 
FTTP (Asset Data Source)
MuleSoft (Integration Layer)
Salesforce (Asset & Work Management)
Einstein Prediction Builder (Failure Prediction)
ServiceNow (Incident Management)
Salesforce Field Service (FSL)
 
The system predicts failure probability daily and automatically triggers downstream service workflows.
 
🏗 Architecture
📁 Architecture Diagram: /architecture/architecture.png
 
 
Components
FTTP – Asset Daily Readings Storage
MuleSoft – Data Retrieval & Injection Layer
Salesforce – Asset Management & Work Orders
Einstein Prediction Builder – Failure Probability Model
ServiceNow – Incident Creation & Knowledge Articles
Salesforce Field Service (FSL) – Field Execution Workflow
 
 
Flow
Step 1 – Asset Data Collection
 
Daily asset readings are stored in FTTP.
 
Step 2 – Integration Layer
 
MuleSoft retrieves daily asset data from FTTP and injects it into Salesforce Asset Objects.
 
Step 3 – AI Failure Prediction
 
Inside Salesforce:
 
Einstein Prediction Builder analyzes asset readings
 
Generates Failure Probability Score (%)
 
Step 4 – Automated Decision Logic
 
Based on the predicted probability:
 
🟡 Case 1: Probability Between 75% – 85%
 
Work Order is automatically created in Salesforce
Work Order Service is initiated
Incident is created in ServiceNow
Knowledge Articles are triggered for internal resolution
Proactive maintenance initiated
 
🔴 Case 2: Probability Greater Than 85%
 
High-priority Work Order is created
Service Appointment (SA) is generated
Salesforce Field Service (FSL) process continues
Field Technician is assigned
Immediate on-site resolution triggered
 
🟢 Case 3: Probability Below 75%
 
Asset marked as Healthy
No work order created
Monitoring continues
 
 
🛠 Tech Stack
| Layer                    | Technology                     |
| ------------------------ | ------------------------------ |
| Data Source              | FTTP                           |
| Integration              | MuleSoft                       |
| CRM Platform             | Salesforce                     |
| AI Model                 | Einstein Prediction Builder    |
| Incident Management      | ServiceNow                     |
| Field Operations         | Salesforce Field Service (FSL) |
