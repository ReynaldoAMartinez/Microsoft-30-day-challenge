# Module 1 — SOC Lab and Sentinel Setup - Days 1-9
___
# Day 1:Created an Azure account to manage the project
___

# Created an Azure account
  <img width="1158" height="360" alt="image" src="https://github.com/user-attachments/assets/20ea78b4-db43-4e45-9716-878c6ef971f1" />

# Set up a billing alert
  <img width="1574" height="383" alt="image" src="https://github.com/user-attachments/assets/6da58d7f-e330-45af-bfd7-04d711dbc8aa" />

# Decided on my resource naming convention: MyDFIR-Reynaldo

___
# Day 2:Create a Windows 11 virtual machine
___
# Created a resource to save my project: MyDFIR-Reynaldo-RG
<img width="1375" height="356" alt="image" src="https://github.com/user-attachments/assets/32cccbbc-67a4-4bd0-9e5a-98c39efcc504" />


# Created a Windows 11 virtual machine in Azure
<img width="1778" height="902" alt="image" src="https://github.com/user-attachments/assets/7ffb84b2-06c6-49ff-978d-a25ce693f063" />

# RDP to the Windows 11 virtual machine
<img width="2552" height="1434" alt="image" src="https://github.com/user-attachments/assets/a74e2291-829a-4721-8379-0a353074a3e6" />


___
# Day 3: Create a Log Analytics Workspace
___
# Create the Log Analytics workspace named MyDFIR-Reynaldo-LAW
<img width="754" height="949" alt="image" src="https://github.com/user-attachments/assets/17080e60-8587-4ef8-8f15-26a1655ccc0d" />

# Install Microsoft Sentinel
<img width="1910" height="940" alt="image" src="https://github.com/user-attachments/assets/fe90e2e9-59b5-43e2-aca7-d73d85edfcd2" />

- Today I learned that **Microsoft Sentinel** allows you to **ingest and centralize logs**, **create custom detections**, and **run automated workflows** using the following options:

  - 📝 **Logs**: Run queries (pre-built). There are two modes to run these queries:
    - 🔹 **Simple mode**
    - 🔹 **KQL mode**
  
  - ⚙️ **Configuration / Analytics**: Create your own **detection rules**.
  
  - 🤖 **Configuration / Automation**: Create **automation rules** that can act as **playbooks**.
  
  - 🚨 **Threat management / Incidents**: Create **incidents** based on **alerts** defined in the Analytics page.
  
  - 📊 **Threat management / Workbooks**: Build **dashboards** and **visualizations**.

___
# Day 4:Connect the first data source to Sentinel, and begin learning KQL (Kusto Query Language)
___
# Connected AzureActivity to Sentinel
Under Azure, updated diagnostics setting to speficies categories: Administrative, Security, and Alert and Send to Log Analytics workspace in Azure subscription 1 to the MyDFIR-Reynaldo-LAW
<img width="1904" height="846" alt="image" src="https://github.com/user-attachments/assets/dd162cc7-0446-42de-a400-4af5c1b13236" />

Now I go to Defender / System / Settings / Microsoft Sentinel  and I can see my workspace “Connected”
<img width="1909" height="942" alt="image" src="https://github.com/user-attachments/assets/650b7824-5972-4d8c-9ead-e31ff5a2c5a6" />

In Microsoft Defender / Content hub I searched for Azure Activity to install it
<img width="1904" height="961" alt="image" src="https://github.com/user-attachments/assets/876e4c97-2854-471f-afd3-56de25160617" />

Then from Azure I installed Microsoft Sentinel Training Lab Solution
<img width="744" height="955" alt="image" src="https://github.com/user-attachments/assets/b2d50130-eb1d-41d5-b875-97f5aa0861fc" />

From Sentinel / Logs, I created my first KQL using one of the tables (SecurityEvent_CL): 
### 🔍 Query: Failed Logon Events

This query returns up to 10 records from the **SecurityEvent_CL** table where the **Event ID** equals `4625` (failed logon attempts).

```kql
SecurityEvent_CL
| where EventID_s == "4625"
| take 10
<img width="1905" height="962" alt="image" src="https://github.com/user-attachments/assets/2618917b-68da-45ba-a121-b87a84eddbea" />


# Day 5:
___
# Day 6:
___
# Day 6:
___
# Day 6:
___
# Day 6:
___



[⬅️ Back to Main Page](../README.md)
