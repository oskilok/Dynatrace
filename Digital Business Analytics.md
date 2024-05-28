# Digital Business Analytics with Dynatrace

## Bridging the Gap to the Business

```
\\TO EDIT
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
```

### Why Bizevents

Business events powered by our new Grail™ data lakehouse and by other Dynatrace platform technologies ensures the real-time precision that business and IT teams need to make data-driven decisions and improve business outcomes. Business events deliver the industry’s broadest, deepest, and easiest access to your critical business data. Powered by Grail, you can now unify, store, and instantly analyze massive volumes of business data from anywhere, automatically enriched with the IT context needed to unlock precise AI-powered answers and automation.


### How Bizevents Works

![alt_text](https://github.com/oskilok/Dynatrace/blob/main/Images/Bizevents.png)

1. Business event sources include OneAgent, web and mobile RUM sessions, external business tools via a public API, and log files.
2. Business events are processed through the ingest pipeline using the Dynatrace Query Language (DQL) to transform and enrich the data and set retention periods.
3. Grail unifies business and IT observability data from all sources, leveraging the Smartscape® dependency model to automatically build causational context.
4. Dynatrace Query Language provides exploratory analytics through ad hoc queries without the need to index. Explore interactively with the Log and event explorer, pin your queries to dashboard tiles, or execute queries via the API.


### Business event capture – Part 1

To capture business events using OneAgent, you need to first enable the feature.
1.	Go to **Settings** > **Preferences** > **OneAgents features**.

2.	Enable the OneAgent business events feature.

![alt text](https://github.com/oskilok/Dynatrace/blob/main/Images/OneAgent%20features.jpg)

> Note: You need to restart the application process before you can capture business events from the process.

 
### Business event capture – Part 2

In this lab, we will use Business event to capture Withdraw business data to Dynatrace
1.	Assess the easyTrade homepage, and login as James Norton.

![alt text](https://github.com/oskilok/Dynatrace/blob/main/Images/login.jpg)

2.	Select **Withdraw** in the Menu.

![alt text](https://github.com/oskilok/Dynatrace/blob/main/Images/Withdraw.jpg)
 
3.	Open DevTools by pressing **Control+Shift+J** or **Command+Option+J** (Mac). The Console panel opens.

4.	Click the **Network** tab. The Network panel opens.

![alt text](https://github.com/oskilok/Dynatrace/blob/main/Images/Network%20Panel.jpg)

5.	Click **AUTOFILL** and then **WITHDRAW**
![alt text](https://github.com/oskilok/Dynatrace/blob/main/Images/Autofill.jpg)

6.	Ingest **Withdraw** business event source via the following in **Settings** > **Business Analytics** > **OneAgent Business Event Sources**:

![alt text](https://github.com/oskilok/Dynatrace/blob/main/Images/Ingestion%20Rule.jpg)

<pre>
- <b>Rule Name</b>: [Easytrade] - Withdraw
- <b>Triggers</b>:
    - <b>Add Trigger</b>:
        - <b>Data Source</b>: Request - Path
        - <b>Operators</b>: ends with
        - <b>Value</b>: withdraw
    - <b>Add Trigger</b>:
        - <b>Data Source</b>: Request - Path
        - **Operators**: starts with
- <b>Event meta data</b>:
    - <b>Event provider</b>
        - <b>Data source</b>: Fixed value
        - <b>Fixed Value</b>: Withdraw
- <b>Event data</b>:
    - <b>Add data field</b>
        - <b>Field name</b>: accountId
        - <b>Data Source</b>: Request - Body
        - <b>Path</b>: accountId
    - <b>Add data field</b>
        - <b>Field name</b>: address
        - <b>Data Source</b>: Request - Body
        - <b>Path</b>: address
    - <b>Add data field</b>
        - <b>Field Name</b>: amount
        - <b>Data Source</b>: Request - Body
        - <b>Path</b>: amount
    - <b>Add data field</b>
        - <b>Field Name</b>: cardNumber
        - <b>Data Source</b>: Request - Body
        - <b>Path</b> - cardNumber
    - <b>Add data field</b>
        - <b>Field Name</b>: cardType
        - <b>Data Source</b>: Request - Body
        - <b>Path</b>: cardType
    - <b>Add data field</b>
        - <b>Field Name</b>: email
        - <b>Data Source</b>: Request - Body
        - <b>Path</b>: email
    - <b>Add data field</b>
        - <b>Field name</b>: name
        - <b>Data Source</b>: Request - Body
        - <b>Path</b>: name
</pre>

> Note:
>  The Trigger is based on the Request URL Path

![alt text](https://github.com/oskilok/Dynatrace/blob/main/Images/Add%20Trigger.jpg)

> The Event data is based on the Request Body as shown in the [architecture diagram](https://github.com/Dynatrace/easytrade/blob/main/docs/broker-service.md#post-v1balanceaccountidwithdraw-withdraw-money-to-the-account)

To validate that the log ingestion rule has been properly set up. 
1. Open **Logs and Events** App
2. Switch to **Advanced mode**
3. Run the following DQL commands

```
fetch bizevents
| filter event.type == "Withdraw"
```
![alt text](https://github.com/oskilok/Dynatrace/blob/main/Images/Logs%20and%20events.jpg)




**Repeat the previous steps for the following:**
- [Buy](https://github.com/Dynatrace/easytrade/blob/main/docs/broker-service.md#post-v1tradebuy-quick-buy)
- [Sell](https://github.com/Dynatrace/easytrade/blob/main/docs/broker-service.md#post-v1tradelongsell-long-sell)
- [Deposit](https://github.com/Dynatrace/easytrade/blob/main/docs/broker-service.md#post-v1balanceaccountiddeposit-deposit-money-to-the-account) 




