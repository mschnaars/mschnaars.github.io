---
title: Setting Item Access Control
summary: "Definitions of item access levels and instructions for assigning special access."
sidebar: avalon6_sidebar
permalink: avalon6_setting_item_access_control.html
folder: avalon6/administration
---

Different levels of access can be assigned at the Item level during an Item's creation. Assigning access control to Items can be useful when Items or Collections need special handling, due to sensitive content, privacy concerns, or legal requirements.

## Definitions

Authenticated User
: {{site.data.definitions.authenticated_user}}

Collection Staff
: {{site.data.definitions.collection_staff}}

Item
: {{site.data.definitions.item}}

## Published vs. Unpublished

The following instructions for setting access Control and granting special access refer specifically to published Items. Unpublished Items, regardless of their access levels, are viewable only by Collection Staff. Leave Items unpublished if their details (metadata, structure, access control, etc.) are not yet finalized.

## Access Control Levels

Access to specific Items is set manually when Items are created.

{% include image.html file="doc_images/access_control.png" alt="access control options" %}

* _Available to the general public_ : anyone can view this Item, even if they are not logged in as an Authenticated User.
* _Logged in users only_ : only Authenticated Users may view this Item, and the Item is not discoverable to the general public.
* _Collection staff only_ : only Collection Staff may view this item.

Additionally, "Hide this item from search results" can be used to make an Item available via URL only, as the Item will not appear using browse or search. This can be useful when the person to whom access is being granted does not have a username or account with Avalon. The item is considered available to the general public, but access is only available through a URL.

## Special Access

Beyond the access control levels defined above, special access can be given to individuals, specific groups of users, and certain IP addresses or range of IP addresses.

{% include image.html file="doc_images/special_access.png" alt="special access controls" %}

* _Avalon User_ : access to an Item can be limited to individual Authenticated Users. Add username(s) to grant access to the Item.
* _Avalon Group_ : access to an Item can be limited to a pre-defined group of Authenticated Users, e.g. members of a class or department. Select the pre-defined group from the drop-down menu to grant access to the Item. If a group needs to be added, contact an Avalon group manager or Administrator.
* _External Group_ : access to an Item can be limited to groups defined by external services, such as a Learning Management System like Canvas or an LDAP group.
* _IP Address or Range_ : access to an Item can be limited to an IP address or range of addresses, e.g. a specific computer lab or group of devices.
  * Examples:
    * 255.0.1.10
    * 255.0.1.10/21
    * 255.0.1.10/255.255.255.0
    * 2001:0db8:85a3:0000:0000:8a2e:0370:7334.

Each type of special access can be further limited to a date range. This can be useful if access should be limited to a short time span (e.g. a week or a month) or a pre-determined set of dates (e.g. the duration of a semester or an eight-week course).

{% include links.html %}