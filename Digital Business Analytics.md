# Digital Business Analytics with Dynatrace

## Bridging the Gap to the Business
 This Repo contains the lab to automate the process

### Prerequisites

* Dynatrace SaaS/Managed Account.
  * Get your free SaaS trial [here](https://www.dynatrace.com/signup/)
* Sample Application
  * Sample Application is based on easyTrade
  * Follow the [Prerequisite Action](https://github.com/Dynatrace/easytrade) to create the application that will be used throughout this workshop 

### What You’ll Learn
-	Understand Real User Monitoring setup with EasyTrade App
-	Learn Digital Business Analytics
-	Learn Dynatrace capabilities, such as
    -	Bizevents via OneAgent
    -	Dynatrace Query Language (DQL)
    -	Gen 3 Dashboard
-	Exporting into Excel and Power BI

### Business event capture – Part 1

To capture business events using OneAgent, you need to first enable the feature.
1.	Go to **Settings** > **Preferences** > **OneAgents features**.

2.	Enable the OneAgent business events feature.

![alt text](https://github.com/oskilok/Dynatrace/blob/main/Images/OneAgent%20features.jpg)

> Note: You need to restart the application process before you can capture business events from the process.

 
### Business event capture – Part 2

In this lab, we will use Business event to capture Withdraw business data to Dynatrace
1.	Assess the easyTrade homepage, and login as James Norton.
``` insert image ``` 

2.	Select Withdraw in the Menu.
``` insert image ```
 
3.	Open DevTools by pressing Control+Shift+J or Command+Option+J (Mac). The Console panel opens.
``` insert image ```

4.	Click the **Network** tab. The Network panel opens.
``` insert image ```

5.	Click **AUTOFILL** and then **WITHDRAW**
``` insert image ```

6.	


