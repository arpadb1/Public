# Azure Sentinel Security Report

**Azure Sentinel Security Report** is a PowerBI dashboard that will help you track your visualize most typical data source ingested into Azure Sentinel. 

The dashboard contains out-of-the-box reports that will help you analyse your security status by providing the necessary information to investigate changes in your score over time.  


## Prerequisite:

1. Power BI account (to open the report as template app you need Pro account). 
2. Power BI desktop intalled (version 2.99.862.0 or higher). This is required only if you chose to use the desktop version.


## **Getting the reports**
For detailed architectural explanation of the solution please refer to [Create a Power BI report from Microsoft Sentinel data](https://docs.microsoft.com/en-us/azure/sentinel/powerbi). 
You can open the reports with two different options:
1. With Power BI Desktop (described under section *Open with Power BI Desktop*).
2. With Power BI Online, if you publish the report from Power BI Desktop to an online workspace  (described under section *Open with Power BI Online*).

## *Open with Power BI Desktop*
1. Download the file *Secure Score Report* Power BI template file from the repository.
2. Open the file using Power BI Desktop.
3. Enter your Log Analytics workspace id and click **Load** button.

    ![Enter log analytics id](https://github.com/arpadb1/Public/blob/main/Hydra/img/LogAnaliticsPowerBIDesktop1.png)

4. Perform authentication using organizational account with **OAuth2** as the authentication method for your Log Analytics workspace.  

5. After authentication completed, the data will be loaded.  
***Note:**  
You visualize only your data if the data already available at the Log Analytics workspace. For further details on data source check the Data Sources section.
6. If you like, you can publish the report to Power BI Online using the next steps.

## *Open with Power BI Online*
For detailed guide please refer to [Create a Power BI online workspace](https://docs.microsoft.com/en-us/azure/sentinel/powerbi#create-a-power-bi-online-workspacei)
To create a Power BI workspace for sharing the report:
1. Sign in to powerbi.com with the same account you used for Power BI Desktop and Microsoft Sentinel read access.
2. Under Workspaces, select Create a workspace. Name the workspace Management Reports, and select Save.
3. To grant people and groups access to the workspace, select the More options dots next to the new workspace name, and then select Workspace access.
4. In the Workspace access side pane, you can add users' email addresses and assign each user a role. The roles are Admin, Member, Contributor, and Viewer.

Once the workspace is created, you can publish the report there:


 ![Publish to Power BI Online](https://github.com/arpadb1/Public/blob/main/Hydra/img/publish.png)
 
 
 Select the right workspace:
 
 
 ![Select Workspace in Power BI Online](https://github.com/arpadb1/Public/blob/main/Hydra/img/select-workspace.png)


## *Import Report to Microsoft Teams*


One cool feature of Teams is the native integration of Power BI online. To display reports in a teams channel, please follow:

[Import the report to a Microsoft Teams channel](https://docs.microsoft.com/en-us/azure/sentinel/powerbi#import-the-report-to-a-microsoft-teams-channel)

## **Reports Content**


### **Data Sources**
Here is the list of data sources you need to connect to have visuals on relevant PowerBI riport tabs

1. **General Event Stats**:  No specific data connector requirement, more or less the replica of Microsoft Sentinel overview page

2. **Logon Stats**:  Security Events 4624 and 4625, connectors Security Events via Legacy Agent or Windows Security Events via AMA

3. **AzureAD Map**: Azure Active Directory connector with Sign-In Logs

4. **AzureAD stats**: Azure Active Directory connector with Sign-In Logs

5. **Data ingestion stats**: No specific data connector requirement 

6. **Azure Activity Logs**: Azure Activity connector

7. **Incidents**: No specific data connector requirement, however enabling Analitics Rules or connecting security producs that create incidents (eg Microsoft Defender ecosystem) is suggested

8. **Office 365**: Office 365 connector including Exhcnage, SharePoint, Teams data sets

9. **Teams**: Office 365 connector Teams data set

10. **AAD PW ProtStat**: Agent collecting logs from domain controllers, Event Source: Microsoft-AzureADPasswordProtection-DCAgent/Admin,  EventID = 30009 or EventID = 30007 or EventID == 10015

11. **AAD Risky Users**: Azure Active Directory Logs, specifically the AADRiskyUsers data


### **PowerBI Tabs explained**
1. **General Event Stats**:
    
    
    This shows Event statistics from different perspectives for the last 7 days. For example, you see time or per machine distribution per type.
    You can apply filters, for example to see this data from a single machine.
    You also see incident distribution.
    
       
    ![ General Event Stats](https://github.com/arpadb1/Public/blob/main/Hydra/img/GeneralEventStats.png)


2. **Logon Stats**:  
    
    
    This shows Logons statistics for the last 30 days based on Security Event ID 4625. Unexpected peaks in time distribution may indicate an attack. 
    High number of failed logons for an account may also indicate an attack or a potential application misconfiguration.
    You see: Distribution of Successful and Failed logon in an hourly basis for the last 30 days, top account attempts, top 10 IP addresses with most logons with success/failure distribution for last 7 days, top 10 success/failed Logon attempt distribution by account and distribution of failure reason for last 7 days
    
    ![ Logon Stats](https://github.com/arpadb1/Public/blob/main/Hydra/img/LogonStats.png)


3. **AzureAD Map**: 


    This shows geographic distribution of AAD Logons. It can be filtered for individual users. Look for strange patterns, unexpected countries.
    
    
    ![ AzureAD Map](https://github.com/arpadb1/Public/blob/main/Hydra/img/AzureADMap.png)


4. **AzureAD stats**: 


    Azure AD Statistics. You can see which applications received the most failed signin, the distribution of signin results and the time distribution of logon attempts.
    

    
    ![ AzureAD stats](https://github.com/arpadb1/Public/blob/main/Hydra/img/AzureADStats.png)


5. **Data ingestion stats**: 


    Usage Statistics. Get a quick understanding of data ingested in the last 30 days by type. Understand top contributors by type / node. 
    Get a quick understand of the distribution of Security Event IDs among the Security Events to point out potentially unwanted, chatty audit categories.


    ![ Data ingestion stats](https://github.com/arpadb1/Public/blob/main/Hydra/img/DataIngestionStats.png)


6. **Azure Activity Logs**: 


    Azure Statistics - brief statistics on the distribution of Azure activities based on Category, user and time distribution.


    ![ Azure Activity Logs](https://github.com/arpadb1/Public/blob/main/Hydra/img/AzureActivityLogs.png)


7. **Incidents**: 
    
    
    Incident Statistics. Understand Incident distribtuion by Time and Product and Severity. Investigate the alert Queue for the last 7 days.
    
    
    ![ Incidents](https://github.com/arpadb1/Public/blob/main/Hydra/img/Incidents.png)
    

8. **Office 365**: 
    
    
    Office 365 Statistics  - brief statistics on the distribution of  activities based on Operation Type, User Type, User, workload and time distribution.
    
    
    ![ Office 365](https://github.com/arpadb1/Public/blob/main/Hydra/img/Office365Stats.png)
    

9. **Teams**: 


    Teams Statistics - brief statistics on the distribution of  activities based on Operation Type, User Type, and time distribution


    ![ Teams](https://github.com/arpadb1/Public/blob/main/Hydra/img/MicrosoftTeamsStats.png)


10. **AAD PW ProtStat**: 


    Azure Ad password protection statistics - statistics on banned passwords


    ![ AAD PW ProtStat](https://github.com/arpadb1/Public/blob/main/Hydra/img/AADPasswordStats.png)
    

11. **AAD Risky Users**:


    This shows users marked as risky in the last 30 days and the distribution of user risk levels.
    In addition, you see the time distribution of risk updates. Peaks of updates may indicate an ongoing attack.
    Note: the same user may receive multiple risk updates, so it can happen that you see more risk update events than users.
    
    
    ![ AAD Risky Users](https://github.com/arpadb1/Public/blob/main/Hydra/img/AADRiskyUsers.png)
