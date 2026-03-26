---
icon: material/numeric-2-box-multiple
icon: material/folder-open-outline

title: Integrate New Salesforce Connector with WebRTC
layout: post
---

# Data Lookup Using CAD Variables

<script>
function copyText(text) {
  navigator.clipboard.writeText(text);
  alert("Copied: " + text);
}
</script>

	
Please use the following credentials to complete the tasks:


| <!-- -->                  | <!-- -->         |
| ------------------------- | ---------------- |
| `Control Hub`             | <a href="https://admin.webex.com" target="_blank">https://admin.webex.com</a> |
| `Salesforce`   | <a href="https://login.salesforce.com" target="_blank">https://login.salesforce.com/</a> |


!!! abstract "Info"
	Utilizing CAD (Call-Associated Data) variables passed from Webex Contact Center enables agents to streamline their workflows and operate more efficiently when addressing customer interactions and requests. These variables provide agents with critical information, such as customer details or interaction context, directly within their interface. By having instant access to this data, agents can reduce the need for manual lookups, save time, and deliver a more personalized and effective customer experience. This not only improves agent productivity but also enhances overall customer satisfaction.

!!! info "Task Objectives"
	- Configure Call Center in Salesforce for advanced screen pop functionality.
	- Customize and publish a Webex Contact Center flow with Salesforce integration.
	- Test the integration by triggering a Salesforce contact creation via a phone call.

## 1. **Salesforce Configuration**

!!! warning "Attention"
	Please use the **Firefox** browser to access, configure, and test within the Salesforce portal.

- Navigate to **'Setup'** by clicking the gear icon in the top-right corner and selecting **'Setup'**

![Nav](./assets/t2s1p1.png){ width="350" }

- Go to **'Feature Settings > Service > Call Center > Call Centers'** (or type _Call Centers_ in the search bar in the left-hand menu).
- Click **'Edit'** for **'WxCC Call Center'**.

![Nav](./assets/t2s3p1.png){ width="800" }

- Under **'Advanced Screen Pop Search Configuration'**, change **'Advanced Screen Pop Enabled'** to **true** (type it in manually).
- For **'CAD Variable Name'**, use **_ani_**.
- Under **'Screen Pop Settings for No Record Match'**, populate **'Object Field Mappings'** as follows:

``` ios
Phone={ani}
```

![Nav](./assets/t3s1p1.png){ width="500" }


- Click **'Save'**.

## 2. **Webex Contact Center Configuration**

- Log in to the <a href="https://admin.webex.com" target="_blank">https://admin.webex.com</a> using the credentials provided at the top of this page.
- Click on Contact Center in the left-hand side navigation pane of the Webex Control Hub. 

![Nav](./assets/t3s2p1aa.png){ width="500" }

- Create 3 Global varibles that are reportable as **caseid**, **description** and **subject**. Similar to below:

![Nav](./assets/t3s2p2.png){ width="500" }

- After logging in, navigate to the **'Flows'** menu on the left-hand side.

![Nav](./assets/t3s2p1.png){ width="200" }

- Download <a href="https://raw.githubusercontent.com/WebexCC-SA/CRM/refs/heads/main/docs/assets/Salesforce_bootcamp_DoNotDelete_Draft.json" target="_blank">this link</a> and save the file by clicking right click and **Save As** a JSON file. Then import the flow provided: 

![Nav](./assets/task4_fllow.png){ width="500" }


- Search for the flow named **Salesforce_bootcamp_DoNotDelete* and open the flow by selecting **Go to Flow Designer** by clicking the icon on the right. 

![Nav](./assets/t3s2p2.png){ width="1000" }


- Turn edit mode by: **'Edit'** is set to **'On'**

![Nav](./assets/t3s2p3.png){ width="800" }

- Click on the queue node and enter the queue name that is setup in your sandbox that will route the call to the agent 

![Nav](./assets/task4_flow_2.png){ width="500" }

- Click on an empty space in the flow, then on the right-hand side, scroll down to navigate to **'Custom Variables > Flow Variables'** section.
- Click on **sfurl** flow variable, select the **'Edit'** option (pencil icon), replace **NN** with the attendee number which is the fully qualified domain name (FQDN) from your Salesforce lab (e.g., _wx1-lab01-dev-ed.develop.lightning.force.com_;) as the Default Value, and click **'Save'**.

!!! warning "Attention" 
	The FQDN used for the **sfurl** variable must end with **.lightning.force.com**. While logged into the Salesforce portal, you can find the name of the Salesforce organization in the browser's address field.
	Note that the Salesforce Setup page will have a different domain ending (it does not end with **.lightning.force.com**). To obtain the correct FQDN, you can either navigate to the Salesforce Sales app and copy the full FQDN from the browser's address field there, or copy the Salesforce organization name from the Salesforce Setup page from the browser's address field and append it with **.lightning.force.com**.

![Nav](./assets/t3s2p5.png){ width="500" }
![Nav](./assets/t3s2p6.png){ width="500" }

- Turn Flow Validation **'On'** by clicking the **'Validation'** button at the bottom of the page to publish the flow. Once validation is complete, click **'Publish Flow'** and then **'Publish Flow'** again in the next dialog box (**Latest** version label is selected automatically).

![Nav](./assets/t3s2p7.png){ width="300" }

- Navigate to the **'Channels'** menu in the Webex Contact Center configuration.

![Nav](./assets/t3s2p8.png){ width="200" }

- Open **WebexOne_AI_EntryPoint_ID** (where **'iD'** is your lab user number, e.g., _labuser**07**@wx1.wbx.ai _), verify that your flow is under 'Routing Flow' 

- Note down the **'Support Number'** associated with this channel - it will be needed later in this lab for testing. 

![Nav](./assets/t3s2p9.png){ width="1000" }



## 3. **Testing**

!!! warning "Attention"
	Please use the **Firefox** browser to access, configure, and test within the Salesforce portal.

- Refresh Salesforce by logging out and logging back in (**make sure to close any other Salesforce tabs**).

![Nav](./assets/t2s4p1a.png){ width="500" }

- Open the Webex Contact Center phone widget and login using the selected Webex Contact Center credentials.
- For the team use **Salesforce Team**.

!!! note "Reminder" 
	Please select the **'Desktop'** option for the phone number.

![Nav](./assets/task2/4.png){ width="500" }

- Make sure that the agent state is set to 'Available' and then call the channel number (noted from the steps above). In the IVR, choose **option 4**.
- Since Salesforce does not recognize your number, a new **Contact** create window will open with the phone number prefilled.
- Provide a name and save the contact in Salesforce.

![Nav](./assets/t3s3p1.png){ width="1000" }

- End the call.
- Wrapup the session, make sure that the agent state is set to 'Available' and make another call. In the IVR, choose **option 4** again.
- This time, the system will open the matching contact, as it was created in the previous step.

![Nav](./assets/t3s3p2.png){ width="400" }

- Congratulations! You have complete the task.
