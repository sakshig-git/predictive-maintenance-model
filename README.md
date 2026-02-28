# 🚀 Predictive Maintenance Matrix(AI Powered Failure Prediction System)
"We don’t wait for failures. We predict them. We prevent them. We power the future." ⚙️📊

## 👥 Team Details

- **Team Name:**  Predictive Maintenance Matrix
- **Members:**
   Sandeep P
   Sakshi Rajesh Gajghate
   Joshi Bhargav Ammavajhala
   Ramanjaneyulu Kurma
   Yogitha Chundu  
- **Domain Category:** AI / Predictive Analytics / Industrial AI    
- **Demo Video:** Sharepoint URL of your MVP demo  

---

## 🎯 Problem Statement

Industrial assets generate daily operational readings. However:
 
Data remains siloed
Failures are detected only after breakdown
Work orders are manually triggered
Field service response is delayed
 
Organizations need an automated, AI-driven failure prediction system that:
Integrates across enterprise platforms
Predicts failure probability
Automatically initiates service workflows

---

## 💡 Solution Overview

Predictive Maintenance Matrix is an enterprise-grade predictive maintenance solution that integrates:
 
FTTP (Asset Data Source)
MuleSoft (Integration Layer)
Salesforce (Asset & Work Management)
Einstein Prediction Builder (Failure Prediction)
ServiceNow (Incident Management)
Salesforce Field Service (FSL)
 
The system predicts failure probability daily and automatically triggers downstream service workflows.

---

## 🏗 Architecture

📁 Architecture Diagram: `/architecture/architecture.png`

### Components

-FTTP – Asset Daily Readings Storage
-MuleSoft – Data Retrieval & Injection Layer
-Salesforce – Asset Management & Work Orders
-Einstein Prediction Builder – Failure Probability Model
-ServiceNow – Incident Creation & Knowledge Articles
-Salesforce Field Service (FSL) – Field Execution Workflow

### Flow

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

---

## 🛠 Tech Stack

| Layer | Technology |
|-------|------------|
| Data Source              | FTTP                           |
| Integration              | MuleSoft                       |
| CRM Platform             | Salesforce                     |
| AI Model                 | Einstein Prediction Builder    |
| Incident Management      | ServiceNow                     |
| Field Operations         | Salesforce Field Service (FSL) |
 

---

## 📂 Project Structure

```
predictive-maintenance-model/
│
├── README.md                          # Project overview & setup guide (Mandatory)
├── requirements.txt                   # Dependencies (if using simulation scripts)
├── .env.example                       # Environment variable template
│
├── architecture/                      # System architecture assets
│   └── predictive_maintenance_architecture.png
│
├── docs/                              # Functional & business documentation
│   ├── Functional_Requirements_Document.pdf
│   ├── Business_Process_Flow.pdf
│
├── integration/                       # MuleSoft configuration (simulation / reference)
│   ├── mule-flow.xml
│   ├── dataweave-transform.dwl
│   └── jwt-oauth-config.md
│
├── salesforce/                        # Salesforce configuration reference
│   ├── objects/
│   │   ├── Telemetry__c.md
│   │   ├── Asset.md
│   │   ├── Work_Order.md
│   │   └── Service_Appointment.md
│   │
│   ├── flows/
│   │   ├── Telemetry_Record_Triggered_Flow.md
│   │   └── Work_Order_Automation_Flow.md
│   │
│   ├── einstein/
│   │   └── Prediction_Model_Config.md
│   │
│   └── field_service/
│       ├── Scheduling_Policy.md
│       ├── Service_Territories.md
│       └── Skills_Config.md
│
├── servicenow/                        # ServiceNow integration reference
│   ├── incident_api_mapping.md
│   └── bidirectional_sync.md
│
├── dashboards/                        # Reporting & ROI visualization
│   ├── Asset_Health_Dashboard.png
│   └── ROI_Dashboard.png
│
├── data/                  # Optional (if sample/test data is required)
│   └── Telemetry Data.csv
```

---

## ⚙️ Setup Instructions

## 1️⃣ Verify Required Software & Platform Access
🔹 Core Platforms Required

Salesforce Org

Products:

Service Cloud

Field Service (FSL)

Einstein Prediction Builder

MuleSoft Anypoint Studio

Version: 7.x or higher

ServiceNow Developer Instance

ITOM enabled

Data Loader (for initial data upload)

## 2️⃣ Clone Repository
git clone https://github.com/sakshig-git/predictive-maintenance-model
cd predictive-maintenance-model

## 3️⃣ Salesforce Configuration Setup
Step 1: Create Custom Object – Telemetry__c

Fields:

Field Name	Type
Vibration__c	Number (2 decimal)
Temperature__c	Number (2 decimal)
Failure_Probability__c	Percent
Is_Failure__c	Checkbox (Training only)
Asset__c	Lookup (Asset)
ServiceNow_Incident_Number__c	Text
ServiceNow_URL__c	URL
Step 2: Create Required Assets

Create Assets:

CNC-Alpha-01

CNC-Beta-05

CNC-Gamma-09

CNC-Delta-02

Ensure each Asset has:

Service Territory

Work Type access

Serial Number populated

Step 3: Train Einstein Prediction Builder

Navigate to:
Einstein Prediction Builder

Select Object:
Telemetry__c

Target Field:
Is_Failure__c

Minimum records:
400+ (for Good rating)

Deploy model

Output field:
Failure_Probability__c

⚠️ Prediction runs asynchronously (~1 minute delay)

## 4️⃣ Configure Record-Triggered Flow

Object: Telemetry__c
Trigger: On Create

Decision Logic:

If Failure_Probability__c > 75%
→ Create Work Order
→ Call ServiceNow API

If Failure_Probability__c > 85%
→ Create Work Order
→ Create Service Appointment

Duplicate Prevention:

Check if an open Predictive Work Order already exists for the same Asset.

## 5️⃣ MuleSoft Configuration
Step 1: Open Anypoint Studio

Import project from:

/integration/mule-flow.xml

Step 2: Configure Salesforce Connector

Use:

JWT OAuth

Connected App credentials

Step 3: Configure File Listener

Batch size: 30

Input:

/data/Telemetry_Data.csv

Step 4: Run Mule Application

Right-click project → Run as Mule Application

## 6️⃣ Configure ServiceNow Integration
Create REST API Endpoint

Endpoint:

/api/now/table/incident

Required Mapping:
Salesforce Field	ServiceNow Field
Work Order Number	correlation_id
Description	short_description
Bi-directional Sync:

When Incident state = Resolved
→ Update Salesforce Work Order status = Completed

## ▶️ Entry Point (System Start)
Start MuleSoft
Run Mule Application

Upload Telemetry CSV

Place file in:

/data/Telemetry_Data.csv


MuleSoft will:

Process 30 records per batch

Insert into Salesforce

## 🔄 Application Flow (End-to-End)

1️⃣ IoT Telemetry CSV uploaded
2️⃣ MuleSoft processes batch of 30
3️⃣ Records inserted into Salesforce
4️⃣ Einstein calculates Failure Probability
5️⃣ Flow evaluates threshold

If 75–85%:
→ Work Order created
→ ServiceNow Incident created

If >85%:
→ Work Order created
→ Service Appointment created

6️⃣ FSL Dispatcher assigns technician
7️⃣ Technician receives mobile notification
8️⃣ Technician completes appointment
9️⃣ Work Order auto-closed
🔟 ROI Dashboard updates

## 🧪 How to Test
Option 1 – Use Sample Dataset

File location:

/data/Telemetry_Data.csv


Upload via:

MuleSoft File Listener

Test Case 1 – Moderate Risk

Input:

Vibration = 8.5
Temperature = 80+


Expected:

Work Order created

No ServiceNow Incident

Test Case 2 – Critical Risk

Input:

Vibration > 9.0
Temperature > 85


Expected:

Work Order created

Service Appointment created

P1 ServiceNow Incident created

Correlation ID populated

Test Case 3 – Incident Closure Sync

Resolve Incident in ServiceNow

Verify:

Salesforce Work Order updates to Completed

## ⚠️ Known Limitations

Einstein scoring delay (~1 minute)

CSV simulation (not live IoT streaming)

ServiceNow integration simulated via API

Duplicate prevention handled via Flow logic

Real-time SLA color logic depends on FSL configuration

## 🔮 Future Improvements

Replace CSV with real IoT streaming (AWS / Azure)

Add Data Cloud for high-volume telemetry

Add GenAI root-cause explanation

Implement Predictive Maintenance LLM assistant

Add real-time SLA breach alerts

Implement automated parts inventory check 
- Add multi-user access management  

---
