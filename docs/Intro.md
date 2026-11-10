---
icon: material/numeric-2-box-multiple
icon: material/folder-open-outline

title: Introduction
layout: post
---

# Introduction 

<script>
function copyText(text) {
  navigator.clipboard.writeText(text);
  alert("Copied: " + text);
}
</script>


!!! info "Task Objectives"
	- This page has the salesforce versions and external guides.
	- How to differentiate between the versions 
	
## Resource links


### 1. Salesforce - Version 1-Legacy  

| <!-- -->                  | <!-- -->         |
| ------------------------- | ---------------- |
| `Integration Guide`             | <a href="https://www.salesforce.com/products/free-trial/developer](https://help.webex.com/en-us/article/nhxw7kfb/Integrate-Webex-Contact-Center-with-Salesforce-(Version-1%E2%80%94Legacy)" target="_blank">https://www.salesforce.com/products/free-trial/developer](https://help.webex.com/en-us/article/nhxw7kfb/Integrate-Webex-Contact-Center-with-Salesforce-(Version-1%E2%80%94Legacy)/</a> |
| `Latest Updates`   | <a href="https://help.webex.com/en-us/article/nhxw7kfb/Integrate-Webex-Contact-Center-with-Salesforce-(Version-1%E2%80%94Legacy)#concept-template_ac93b49e-a5eb-4942-a734-26c8da471aae" target="_blank">https://help.webex.com/en-us/article/nhxw7kfb/Integrate-Webex-Contact-Center-with-Salesforce-(Version-1%E2%80%94Legacy)#concept-template_ac93b49e-a5eb-4942-a734-26c8da471aae/</a> |


### 2. Salesforce - Version 2-New

| <!-- -->                  | <!-- -->         |
| ------------------------- | ---------------- |
| `Integration Guide`             | <a href="https://help.webex.com/en-us/article/dyidod/Integrate-Webex-Contact-Center-with-Salesforce-(Version-2-New)" target="_blank">https://help.webex.com/en-us/article/dyidod/Integrate-Webex-Contact-Center-with-Salesforce-(Version-2-New)/</a> |
| `Access Guide`   | <a href="https://help.webex.com/en-us/article/n08vfjcb/Access-and-use-Webex-Contact-Center-within-Salesforce-(Version-2-New)" target="_blank">https://help.webex.com/en-us/article/n08vfjcb/Access-and-use-Webex-Contact-Center-within-Salesforce-(Version-2-New)/</a> |
| `Latest Updates`   | <a href="https://help.webex.com/en-us/article/dyidod/Integrate-Webex-Contact-Center-with-Salesforce-(Version-2-New)#concept_d3z_st5_hgc" target="_blank">https://help.webex.com/en-us/article/dyidod/Integrate-Webex-Contact-Center-with-Salesforce-(Version-2-New)#concept_d3z_st5_hgc/</a> |



### 3. Differentiate between versions 

| <!-- -->                  | <!-- -->         |
| ------------------------- | ---------------- |
| `Guide`             | <a href="https://techzone.cisco.com/t5/Contact-Center-3rd-Party/Playbook-CRM-Connector-Version-Matrix-Install-Store-Link/ta-p/16910365" target="_blank">https://techzone.cisco.com/t5/Contact-Center-3rd-Party/Playbook-CRM-Connector-Version-Matrix-Install-Store-Link/ta-p/16910365/</a> |


### 4. Installed Package Verification

- In Salesforce, navigate to **'Setup'** by clicking the gear icon in the top-right corner and selecting **'Setup'**.

![Nav](./assets/t2s1p1.png){ width="350" }

- In the Salesforce portal, navigate to **Apps > Packagin > Installed Packahges** (or type _Installed Packages_ in the search bar above the left-hand menu).

![Nav](./assets/intro_1.png){ width="1000" }


### 5. Helping Customers Gather Redux Logs for New (v2) CRM Connector 

- In Salesforce, Agent desktop widget select the avatar icon on top right and hit **Upload logs**

![Nav](./assets/t2s1p111.png){ width="350" }

- Once they hit the button a **Feedback ID** is generated and we can ask customers to save the ID and provide or if they can note the time the option was selected

![Nav](./assets/t2s1p11122.png){ width="350" }

- Within **Control Hub** > **Troubleshooting** > **Logs** - enter the impacted agents email ID or the **Feedback ID** that was provided in the previous step and download the redux logs 

![Nav](./assets/t2s1p111223.png){ width="1000" }

- Once downloaded you can upload this on the redux tool parser tool view the logs: <a href="https://scripts.cisco.com/ui/use/redux_parser" target="_blank">https://scripts.cisco.com/ui/use/redux_parser</a>   
![Nav](./assets/t2s1p1112234_scv.png){ width="500" }



### 6. Helping Customers Gather Redux Logs for Service Cloud Voice (SCV) 

- In Salesforce, navigate to **'Setup'** by clicking the gear icon in the top-right corner and selecting **'Setup'**.

![Nav](./assets/t2s1p1.png){ width="250" }

- In the Salesforce portal, navigate to **Apps > Packagin > Installed Packahges** (or type _Installed Packages_ in the search bar above the left-hand menu).
- The Package name should be **Webex Contact Center for Service Cloud Voice** indicating its SCV and **Version Number** needs to be **1.3** (lower version will not have the ability to gather logs this way)

![Nav](./assets/intro_12.png){ width="1000" }

- In Salesforce, Agent desktop widget select the gear icon on the top right (Note: Please make sure the agent is signed in under the **Phone** tab)

![Nav](./assets/t2s1p1111.png){ width="250" }

- Scroll down to the bottom and select **Upload logs** (Note: Please make sure the agent is signed in under the **Phone** tab first. If not, the this step will fail with _Error: Log file failed to save. Error: Webex Core is not initialized._)

![Nav](./assets/t2s1p11122_scv.png){ width="350" }

- Once you hit the button, the file will be downloaded and also a **Feedback ID** generated 

![Nav](./assets/t2s1p11122333_scv.png){ width="350" }

- Within **Control Hub** > **Troubleshooting** > **Logs** - enter the impacted agents email ID or the **Feedback ID** that was provided in the previous step and download the redux logs 

![Nav](./assets/t2s1p111223.png){ width="1000" }

- Once downloaded you can upload this on the redux tool parser tool view the logs: <a href="https://scripts.cisco.com/ui/use/redux_parser" target="_blank">https://scripts.cisco.com/ui/use/redux_parser</a>   

![Nav](./assets/t2s1p1112234_scv.png){ width="500" }
