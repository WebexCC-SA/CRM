---
icon: material/numeric-2-box-multiple
icon: material/folder-open-outline

title: Integrate New Salesforce Connector with WebRTC
layout: post
---

# Presence Synchronization Between Salesforce and Webex Contact Center

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
	Presence is crucial for agent productivity, especially when handling multiple contacts across different platforms. 
 	This task focuses on achieving presence synchronization between Webex Contact Center and Salesforce to ensure agents are utilized efficiently.

!!! info "Task Objectives"
	- Configure Salesforce presence statuses to match Webex Contact Center idle codes.
	- Enable presence statuses for the appropriate user profile.
	- Set up Omni-Channel state synchronization in Webex Contact Center settings.
	- Test state sync between Salesforce Omni-Channel and Webex Contact Center.
	- The same steps can be used for both Legacy (Version 1) connector or New (Version-2) connector. The screenshots here are shown for New (Version-2) connector

## 1. **Create Presence Statuses**

!!! warning "Attention"
	Please use the **Firefox** browser to access, configure, and test within the Salesforce portal.


!!! note
	For presence synchronization to work between Salesforce and Webex Contact Center, the idle code names in Webex Contact Center must match the presence state names in Salesforce.


- In Salesforce, navigate to **'Setup'** by clicking the gear icon in the top-right corner and selecting **'Setup'**.

![Nav](./assets/t2s1p1.png){ width="350" }

- Go to **'Feature Settings > Service > Omni-Channel > Omni-Channel Settings'** (or type _Omni-Channel Settings_ in the search bar in the left-hand menu) and enable the below settings highlighted in red and **Save**.

![Nav](./assets/task3_1.png){ width="1000" }

- Go to **'Feature Settings > Service > Omni-Channel > Service Channels'** (or type _Service Channels_ in the search bar in the left-hand menu)

![Nav](./assets/task3_2.png){ width="800" }

- Edit 	Service Channel Name Phone and update the **Capacity Settings** to **Status Based** and hit **Save**

![Nav](./assets/task3_3.png){ width="800" }

- Go to **'Feature Settings > Service > Omni-Channel > Presence Statuses'** (or type _Presence Statuses_ in the search bar in the left-hand menu).

![Nav](./assets/t2s1p2.png){ width="800" }

- Create  two new **Presence Statuses**:
	- Click **'New'**.
	- Provide the name **wxccbusy** under **'Status Name'** and select **'Busy'** under **'Status Options'**.
	- Click **'Save'** and select **`Back to List: Service Presence Statuses'**
	- Create another **Presence Status** with the same options but use **sfbusy** under **'Status Name'**.

![Nav](./assets/t2s1p3.png){ width="500" }
![Nav](./assets/t2s1p4.png){ width="500" }


## 2. **Enable Presence Statuses for the User Profile** 

- Navigate to **'Users > Profiles'** (or type _Profiles_ in the search bar in the left-hand menu).
- Locate the **'System Administrator'** profile (select **`Next`** at the bottom to go to the next page) and click on it (do not click **'Edit'**).

!!! note
	For the purpose of this exercise, the **'System Administrator'** profile is used. Under normal circumstances, any other profile may be used by users.

![Nav](./assets/t2s1p5.png){ width="800" }

- In the next window, hover over **'Enabled Service Presence Status Access'** and click **'Edit'**.

![Nav](./assets/t2s1p6.png){ width="800" }

- Move **Availble**, **sfbusy** and **wxccbusy** from **'Available Service Presence Statuses'** to **'Enabled Service Presence Statuses'**.

![Nav](./assets/t2s1p7.png){ width="600" }

- Click **'Save'**.


## 3. **Configure Omni-Channel State Sync in Call Center Settings**

- Navigate to **'Feature Settings > Service > Call Center > Call Centers'** (or type _Call Centers_ in the search bar in the left-hand menu).
- Click **'Edit'** for **'WxCC Call Center'**.

![Nav](./assets/t2s3p1.png){ width="800" }

- Under **'Omni-Channel State Sync Configuration'**, do the following:
	- Set **'Enable Omni-Channel Sync'** to **true** (type it in manually).
	- For **'Omni-Channel Not Ready Reason'**, type **wxccbusy**.
	- For **'WxCC Idle Reason Code'**, type **sfbusy**.

!!! note
	**'Omni-Channel Not Ready Reason'** is the name of the Salesforce Omni-Channel "Busy" reason status used when the agent receives an inbound call in Webex Contact Center.
 	**'WxCC Idle Reason Code'** is the name of the Webex Contact Center Idle code used when the agent receives an inbound chat in Salesforce.

![Nav](./assets/t2s3p2.png){ width="500" }

- Click **'Save'**.

!!! note
	For the purpose of this lab, the idle code **sfbusy** has already been created on the Webex Contact Center side.


##  4. **Webex Contact Center Configuration**

- Log in to the <a href="https://admin.webex.com" target="_blank">https://admin.webex.com</a> using the credentials provided at the top of this page.
- Click on Contact Center in the left-hand side navigation pane of the Webex Control Hub. 

![Nav](./assets/t3s2p1aa.png){ width="500" }

- After logging in, navigate to the **'Idle/Wrap-up Codes'** menu on the left-hand side and select Create an **Idle/Wrap-up Codes**

![Nav](./assets/task3_4.png){ width="400" }


- Create an idle code **sfbusy** and select **Create**

![Nav](./assets/task3_5.png){ width="400" }

!!! note
	Please make sure that the idle code is added to the desktop profile under **'Idle/Wrap-up Codes'**



##  5. **Testing Omni Sync Presence**


!!! warning "Attention"
	Please use the **Firefox** browser to access, configure, and test within the Salesforce portal.

- Refresh Salesforce by logging out and logging back in (**make sure to close any other Salesforce tabs**).

![Nav](./assets/t2s4p1a.png){ width="500" }


!!! note "Reminder" 
	Please select the **'Desktop'** option for the phone number.

- Open the Webex Contact Center widget (**Phone**) and change the states (e.g., _sfbusy_, _available_) — the Salesforce **Omni-Channel** widget status should follow accordingly.
- Test changing the state from the Salesforce **Omni-Channel** widget — the Webex Contact Center widget should follow as well.

!!! note
	**'Omni-Channel Not Ready Reason'** is the name of the Salesforce Omni-Channel "Busy" reason status used when the agent receives an inbound call in Webex Contact Center. Therefore, the **wxccbusy** state on the Omni-Channel widget will only appear when an agent is actively engaged in a Webex Contact Center call (this will be tested in the next tasks)

![Nav](./assets/t2s4p2a.png){ width="333" }
![Nav](./assets/t2s4p2b.png){ width="347" }

- Congratulations! You have completed the task.

## 6. Troubleshooting Failed Sync Due to Mismatched Idle Codes


- In Salesforce, navigate to **'Setup'** by clicking the gear icon in the top-right corner and selecting **'Setup'**.

![Nav](./assets/t2s1p1.png){ width="350" }

- Go to **'Feature Settings > Service > Omni-Channel > Presence Statuses'** (or type _Presence Statuses_ in the search bar in the left-hand menu).

- Select **'Edit'** the Presence Status **sfbusy** created before 

![Nav](./assets/t3s41p1.png){ width="700" }

- Update **sfbusy** to **Sfbusy** (capitalizing the letter S) and click **'Save'**.

![Nav](./assets/t3s41p2.png){ width="700" }

- Refresh Salesforce by logging out and logging back in (**make sure to close any other Salesforce tabs**).

![Nav](./assets/t2s4p1a.png){ width="500" }

- Open the Webex Contact Center widget (**Phone**) and change the states to **'Available'** — the Salesforce **Omni-Channel** widget status will be changed to **'Available'**

![Nav](./assets/t3s41p3.png){ width="400" }

- Test changing the state from the Salesforce **Omni-Channel** widget to **Sfbusy** and notice thatthe Webex Contact Center widget still shows as  **'Available'**

![Nav](./assets/t3s41p4.png){ width="400" }

!!! warning "Reason" 
    When presence status on **sfbusy** is updated to **Sfbusy**, presence sync becasue idle code on WxCC is **sfbusy**. 
	Omni-channel codes created on Salesforce and in Webex Contact Center needs to match in spelling and in case. 
    Please refer to the [_Omni-Channel State Sync Configuration_](https://help.webex.com/en-us/article/dyidod/Integrate-Webex-Contact-Center-with-Salesforce-(Version-2-New)#reference-template_2cf241c7-ade1-49d6-9582-b38467cb85f4) section for the external documentation  

- Congratulations! You have completed the task.

