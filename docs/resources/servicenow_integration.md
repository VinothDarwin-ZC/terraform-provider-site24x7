---
layout: "site24x7"
page_title: "Site24x7: site24x7_servicenow_integration"
sidebar_current: "docs-site24x7-servicenow-integration"
description: |-
Create and manage a ServiceNow integration in Site24x7.
---

# Resource: site24x7\_servicenow\_integration

Use this resource to create, update, and delete ServiceNow integration in Site24x7.

## Example Usage

```hcl

// ServiceNow API doc - https://www.site24x7.com/help/api/#create-servicenow
resource "site24x7_servicenow_integration" "servicenow_integration" {
  // (Required) Display name for the ServiceNow Integration.
  name = "ServiceNow Integration - Terraform"
  // (Required) ServiceNow instance URL.
  instance_url = "https://www.example.com"
  // (Required) Name of the service who posted the incident.
  sender_name = "Site24x7 - Terraform"
  // (Required) Title of the incident.
  title = "$MONITORNAME is $STATUS"
  // (Required) User name for authentication
  user_name                        = "username"
  // (Required) Password for authentication
  password                        = "password"
  // (Optional) Resource Type associated with this integration. Default value is '0'. Can take values 0|1|2|3. '0' denotes 'All Monitors', '1' denotes 'Monitor Group', '2' denotes 'Monitors', '3' denotes 'Tags'
  selection_type = 0
  // (Optional) Setting this to 'true' will send alert notifications to this third-party integration when the monitor status changes to 'Trouble'. One among trouble_alert|critical_alert|down_alert should be set to true for receiving notifications. Default value is 'true'.
  trouble_alert = true
  // (Optional) Setting this to 'true' will send alert notifications to this third-party integration when the monitor status changes to 'Critical'. One among trouble_alert|critical_alert|down_alert should be set to true for receiving notifications.
  critical_alert = false
  // (Optional) Setting this to 'true' will send alert notifications to this third-party integration when the monitor status changes to 'Down'. One among trouble_alert|critical_alert|down_alert should be set to true for receiving notifications.
  down_alert = false
  // (Optional) Configuration to send custom parameters while executing the action.
  send_custom_parameters = true
  // (Optional) Mandatory, if send_custom_parameters is set as true. Custom parameters to be passed while accessing the URL.
  custom_parameters               = "{\"test\":\"abcd\"}"
  // (Optional) Monitors to be associated with the integration when the selection_type = 2.
  monitors                        = ["756"]
  // (Optional) Tags to be associated with the integration when the selection_type = 3.
  tags                        = ["345"]
  // (Optional) List of tag IDs to be associated with the integration.
  alert_tags_id                   = ["123"]
  // (Optional) Receive alert As - Alert format preference. Specify how you'd like to receive alerts:
  // 1 for Incidents, 2 for Events.
  is_incident_api               = 2
}

```

## Attributes Reference


### Required

* `name` (String) Display name for the ServiceNow Integration.
* `instance_url` (String) ServiceNow instance URL.
* `sender_name` (String) Name of the service who posted the message.
* `title` (String) Title of the incident.
* `user_name` (String) User name for authentication.
* `password` (String) Password for authentication.

### Optional

* `id` (String) The ID of this resource.
* `selection_type` (Number) Resource Type associated with this integration. Default value is '0'. Can take values 0|1|2|3. '0' denotes 'All Monitors', '1' denotes 'Monitor Group', '2' denotes 'Monitors', '3' denotes 'Tags'. Please refer [API documentation](https://www.site24x7.com/help/api/#resource_type_constants).
* `trouble_alert` (Boolean) Setting this to 'true' will send alert notifications to this third-party integration when the monitor status changes to 'Trouble'. One among trouble_alert|critical_alert|down_alert should be set to true for receiving notifications.  Default value is 'true'.
* `critical_alert` (Boolean) Setting this to 'true' will send alert notifications to this third-party integration when the monitor status changes to 'Critical'. One among trouble_alert|critical_alert|down_alert should be set to true for receiving notifications.
* `down_alert` (Boolean) Setting this to 'true' will send alert notifications to this third-party integration when the monitor status changes to 'Down'. One among trouble_alert|critical_alert|down_alert should be set to true for receiving notifications.
* `send_custom_parameters` (Boolean) Configuration to send custom parameters while executing the action.
* `custom_parameters` (String) Mandatory when `send_custom_parameters` is set as true. Custom parameters to be passed while accessing the URL.
* `monitors` (List of String) Monitors to be associated with the integration when the selection_type = 2.
* `tags` (List of String) Tags to be associated with the integration when the selection_type = 3.
* `alert_tags_id` (List of String) List of tags to be associated with the integration.

Refer [API documentation](https://www.site24x7.com/help/api/#create-servicenow) for more information about attributes.


