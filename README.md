# MerakiNodeRedUIDashboard

Cisco Meraki Node-RED Dashboard: Guide

**Overview**

This Node-RED flow provides a example dashboard for monitoring Cisco Meraki organizations, networks, devices, and clients using . It allows users to:

- **Select and view organizations** and networks from their Meraki environment.
- **Monitor Meraki device statuses**, including detailed views for MX devices.
- **Display network device statuses** and wireless latency in real-time using tables and gauges.
- **Visualize wireless connection summaries** with bar charts.
- **List connected network clients** with statuses and MAC addresses.
- **Interact with the dashboard** to refresh data and select particular devices/networks.

The flow integrates with the Cisco Meraki Dashboard API to fetch organization, network, device, and client data, presenting it with rich UI elements (dropdowns, tables, charts) suitable for network monitoring and troubleshooting.

Each flow contians a "Create Unique URL" Node that is used to specify the API Endpoint you want to call based on the OpenAPI Spec Endpoints noted here https://developer.cisco.com/meraki/api-v1/overview/. The purpose of this is for you to have the ability to adjust the endpoints you call as the Meraki API changes and evolves in the future and you are not limited to a potetnialy out of date pre-defined set of calls.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Prerequisites**

Before using this flow, ensure you have:


1. **A Cisco Meraki account** with API access enabled.
2. **A Meraki API key** with appropriate read permissions.
3. **Node-RED installed** (see Node-RED documentation).

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Required Node-RED Palettes**

Install the following Node-RED palettes before importing this flow:

[node-red-dashboard
](https://flows.nodered.org/node/node-red-dashboard)
For UI elements (charts, tables, dropdowns, gauges).

[node-red-node-ui-table
](https://flows.nodered.org/node/node-red-node-ui-table) (optional, if you want advanced tables)

To install, run:

bash

cd ~/.node-red

npm install node-red-dashboard

**Or use the Manage Palette option in Node-RED’s menu.**

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Importing and Using the Flow**

1. Import the Example.json JSON File

Open the Node-RED editor (usually at http://localhost:1880/).
Click the menu (top right) → Import.
Paste the contents of the Example.json file, or upload it directly.
Click Import to add it to your workspace.

2. Deploy the Flow

Click the Deploy button (top right) to activate the flow.

3. Set Your Meraki API Key

Locate any http request nodes (labelled "Auth Token Header") in the flow.
Open each node and set the Authentication to Bearer and paste your Meraki API key, or edit the headers to include:
X-Cisco-Meraki-API-Key: YOUR_API_KEY
Alternatively, set a global/flow environment variable if you use the same key in multiple places.

4. Open the Dashboard

Go to http://localhost:1880/ui (or your Node-RED UI endpoint).
You should see the Demo Dashboard tab with sections for:
Organization and Network selectors
Device statuses and details
Wireless latency and connection summaries
Network clients table

5. Using the Dashboard

**Select an Organization:** Use the dropdown to pick your Meraki organization.
**Select a Network:** Networks will populate based on your organization selection.
**View Device Statuses:** Device tables and charts update automatically.
**Monitor Wireless Latency:** See live wireless latency metrics.
**Review Clients:** Check connected clients and their statuses.
**Refresh Data:** Use provided buttons to refresh client lists or other data as needed.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Notes & Troubleshooting**

**API Limits:** The Meraki Dashboard API has rate limits (10 Calls per second per Org ID); avoid rapid repeated refreshes.

**Authentication:** If API requests fail, double-check that your API key is correct and has sufficient permissions.

**Customization:** You can adjust polling intervals, UI layout, or add custom logic as needed.

**Security:** Never commit your API key to public repositories.

Constants:

This flow is designed for Cisco Meraki environments.
Requires the Node-RED Dashboard palette.
API key must be kept secure.

Edge Cases

If your Meraki organization has no networks/devices, the dropdowns may appear empty.
The dashboard assumes devices return the expected JSON structure; custom networks may need flow adjustments.

Feel free to fork and adapt for your environment!
