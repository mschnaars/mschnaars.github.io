---
title: Item Access Control
summary: "Definitions of item access levels and instructions for assigning special access."
sidebar: avalon6_sidebar
permalink: avalon6_item_access_control.html
folder: avalon6/managing_content
---

{{site.data.alerts.info}}
Access control and special access refer specifically to published items. Unpublished items, regardless of their access control level, are available to collection staff only.
{{site.data.alerts.end}}

## Definitions

Authenticated User
: {{site.data.definitions.authenticated_user}}

Collection Staff
: {{site.data.definitions.collection_staff}}

Item
: {{site.data.definitions.item}}

## Default Access Control

{% include image.html file="doc_images/access_control.png" alt="access control options" max-width="850" %}

### Item Discovery

__Hide this item from search results__
: The item is available via URL only, and does not appear through search or browse. Choose this option when the item needs restriction, but the person to whom access is being granted is not an authenticated user.

### Item Access

Access control is assigned when items are created.

__Available to the general public__
: Anyone can view this item, even if they are not logged in as an authenticated user.

__Logged in users only__
: Only authenticated users may view this item.

__Collection staff only__
: Only collection staff may view this item.

## Special Access

Beyond the access control levels defined above, special access can be given to individuals, specific groups of users, and certain IP addresses or range of IP addresses. Assigning special access is useful when individual items need special handling, due to sensitive content, privacy concerns, legal requirements, etc.

{% include image.html file="doc_images/special_access.png" alt="special access controls" max-width="850" %}

__Avalon User__
: Access is granted to individual authenticated users. Enter a username/email address to grant access.

__Avalon Group__
: Access is granted to a pre-defined group of authenticated users (e.g. members of a class or department). Select a group from the list to grant access. If a group needs to be added, contact an Avalon administrator.

__External Group__
: Access is granted to a group defined by an external services (e.g. Learning Management System or LDAP).

__IP Address or Range__
: Access is granted to an IP address or range of addresses (e.g. computer lab or group of devices).
  
  * Examples:
    * 255.0.1.10
    * 255.0.1.10/21
    * 255.0.1.10/255.255.255.0
    * 2001:0db8:85a3:0000:0000:8a2e:0370:7334.

Special access can be further limited using a date range. Setting a date range is useful if access should be limited to a short time span (e.g. a week or a month) or a pre-determined date range (a semester or eight-week course).

{{site.data.alerts.warning}}
Leaving <b>Begin Date</b> empty will default to the current date, but <b>End Date</b> is required for date ranges.
{{site.data.alerts.end}}

{% include links.html %}