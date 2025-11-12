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
### Query: Failed Logon Events

This query returns up to 10 records from the **SecurityEvent_CL** table where the **Event ID** equals `4625` (failed logon attempts).

```kql
SecurityEvent_CL
| where EventID_s == "4625"
| take 10
```
<img width="1905" height="962" alt="image" src="https://github.com/user-attachments/assets/2618917b-68da-45ba-a121-b87a84eddbea" />

___
# Day 5:Create a Microsoft Sentinel Workbook 
___
From Sentinel / Threat management / Workbooks, I created my own visualizations. One of them is showed below.
<img width="919" height="925" alt="image" src="https://github.com/user-attachments/assets/27f80a06-fd4b-48fb-8b0d-af5d425412ff" />
Something I learned is the dashboard should be created focus on 3 things:

Visibility --> can you see what is happening across your endpoints, users, email?
Volume --> can you track how much activity is occurring?
Trends --> can you detect if something is increasing or changing over time?

___
# Day 6:Connect Microsoft Defender XDR into Sentinel and create a simple analytic rule
___
To connect these two together, I needed to install the appropiate data connector.
<img width="1864" height="958" alt="image" src="https://github.com/user-attachments/assets/5718ee92-6477-45d7-b62d-37c32092d9f2" />

To create a detection rule using the sample data ingested previously I went to Sentinel / Configuration / Analytics / Create / Schedule query rule
<img width="1262" height="880" alt="image" src="https://github.com/user-attachments/assets/df5c3f30-cc2f-4ee4-9317-e8b1a9a8fd00" />


___
# Day 7:Use KQL to investigate a common SOC scenario 
___
This was a great exercise to use the sample log in Sentinel and KQL to investigate a common SOC scenario which is a spike and failed login attempts.
**Scenario**: I received an alert about multiple failed logins. My task is to use KQL to answer the following:
- Which accounts are experiencing the most failed logons?
- Were there any successful logins for those accounts? If so, from where?
- What would I recommend if this were a real client incident?

Please see my investigation report in the next link
## 📄 PDF Resources

- [Open Sentinel Lab Report (PDF)](./docs/InvRepDay7.pdf)

___
# Day 8: Creat Bookmarks in Sentinel to document important findings
___
What I learned about Bookmarks is ...
- it is used during threat hunting or correlation between email and point an identity logs.
- it is listed under Sentinel / Hunting.
- an incident can be created from a bookmark.

I created a KQL to list some data from the table SecurityAlert, create a bookmar, and an incident as it is showed below:
```kql
SecurityAlert
| project TimeGenerated, AlertName, AlertSeverity, CompromisedEntity, ProviderName
| limit 20
```
<img width="1323" height="860" alt="image" src="https://github.com/user-attachments/assets/2456f704-1a20-4656-92b1-e21b3e6d208a" />

<img width="1620" height="444" alt="image" src="https://github.com/user-attachments/assets/ae92d8fe-96f9-4e59-8bf2-1f61cb481146" />

___
# Day 9: Mini Project #1
___
In this point, the assigment is to do a summary of the results achieved after I have completed the Module 1: Days 1-9.

## 🏁 Final Reflection

### 💡 What I Can Now Do That I Couldn’t Before
- ☁️ Build a **cloud-based lab** in Azure  
- 💻 Create **virtual machines** in Azure to work in a safe environment  
- 🧾 Create **Azure accounts** and set up **billing alerts**  
- 📈 Create a **Log Analytics Workspace** in Azure  
- 🛡️ Install and set up **Microsoft Sentinel** and **Defender for Endpoint**  
- 🔍 Create and run **KQL queries** to investigate common SOC scenarios  
- 📊 Create **Dashboards / Workbooks** in Microsoft Sentinel  
- 🔗 Connect **Microsoft Defender XDR** to Sentinel and create simple **analytic rules**  
- 📘 Create **Bookmarks** in Sentinel to document findings  
- 🚨 Create **Incidents** from Bookmarks  

---

### 🌟 Most Impactful Part of the Challenge
> Working all these days in a **real cloud-based environment** using **Microsoft Azure**, **Defender**, and **Sentinel** has been a **huge step** in my learning journey.

---

### 🚀 Areas I Want to Keep Improving
Continue learning about:
- 🧠 **Advanced KQL** & Data Analysis  
- 📚 **Writing and documenting playbooks**  
- 📊 Using **Workbooks** for visual dashboards  
- ⚙️ **Building Sentinel analytic rules**  
- 🧾 Writing clear and concise **SOC investigation reports**





[⬅️ Back to Main Page](../README.md)
