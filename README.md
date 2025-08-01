# service-now-urgent-incident-notification-workflow
## System Overview
After a high-impact outage in Uber’s San Francisco data center exposed a breakdown in critical incident notifications, I was tasked with remediating the existing ServiceNow workflow responsible for alerting the Network Operations team. The original flow failed to trigger notifications for high-priority network incidents. I reconfigured the trigger conditions to target incidents with Priority = 1 and Category = Network, updated the notification details for clarity and alignment, and verified that alerts were sent within SLA thresholds. The renamed Critical Network Incident Notifications workflow now sends out targeted emails to the right group in under a minute, closing the communication gap before it becomes a crisis.

![Workflow Diagram](https://github.com/BerlynseaTyler/service-now-urgent-incident-notification-workflow/blob/main/Images/Overview%20of%20Critical%20Network%20Incident%20Flow.png?raw=true)

## Implementation Steps

### Original Broken Workflow
#### Trigger
![Original Trigger](https://github.com/BerlynseaTyler/service-now-urgent-incident-notification-workflow/blob/main/Images/og_kura_wl1_flow_-_trigger.png?raw=true)
#### Action 
![Orignal Action](https://github.com/BerlynseaTyler/service-now-urgent-incident-notification-workflow/blob/main/Images/og_kura_wl1_flow_-_action.png?raw=true)

### Corrective Actions
1. Renamed the workflow to be more aligned and business appropriate – **Critical Network Incident Notifications**
2. Corrected the trigger by setting the conditions to be – **Priority = 1** and **Category = Network**
3. Corrected the action by fixing the attached notifications with the following steps:

> a. Renamed the notification to – **Critical Incident Notification**
> 
> b. Changed the **Groups** under **Who will recieve** to – **Networking Operations**
> 
> *Note: My instance did not include any members in Networking Operations, so I manually added them.*
> ![Networking Group Members](https://github.com/BerlynseaTyler/service-now-urgent-incident-notification-workflow/blob/main/Images/Networking%20Group%20Members.png?raw=true)
>
> c. Updated the message subject line & body to be more appropriate to the business use case of notifying a team of new critical network incidents, ensuring to include a link to the incident for ease of access.
>  ![Message Body](https://github.com/BerlynseaTyler/service-now-urgent-incident-notification-workflow/blob/main/Images/Notification%20Message%20Body.png?raw=true)

#### Testing 
1. Submitted several test incidents matching the workflow criteria to ensure the new notifications met company SLA standards.
   > ![Test Incidents](https://github.com/BerlynseaTyler/service-now-urgent-incident-notification-workflow/blob/main/Images/Test%20Incidents.png?raw=true)
2. Ensured the email will be sent within 5 minutes of the creation of the new incident.
   > ![Email Confirmations](https://github.com/BerlynseaTyler/service-now-urgent-incident-notification-workflow/blob/main/Images/Email%20Confirmations.png?raw=true)
   > 
   > ![Email Preview](https://github.com/BerlynseaTyler/service-now-urgent-incident-notification-workflow/blob/main/Images/Email%20Preview.png?raw=true) 

### Results 
The updated workflow successfully notified all members of the networking operations group within 1 minute of submission, adhereing to the company's SLAs.

## Architecture Diagram

![Diagram](https://github.com/BerlynseaTyler/service-now-urgent-incident-notification-workflow/blob/main/Diagram.png?raw=true)


## AI Scenario
As Uber takes the market position as the go-to ride share platform across time zones and continents, critical incidents don’t follow a 9-to-5 PST schedule and neither should our response strategy. Today’s escalation paths don't account for who’s actually available or best suited to handle a specific issue. Integrating AI into the notification workflow could change that. An intelligent agent can use real-time data to route incidents to engineers who are not only online, but skilled in the affected system and have resolved similar issues before. It could assess the current on-call shift, prioritize availability by workload and time zone, and reroute to another engineer if there's no response within minutes. Over time, the agent could learn from these incidents to optimize it's routing logic. 

This approach would improve SLA compliance and help prevent service disruptions **before** they affect our customer's experience. 



