---
title: Setting Item Access Control
summary: "Definitions of item access levels and instructions for assigning special access."
sidebar: avalon6_sidebar
permalink: avalon6_setting_item_access_control.html
folder: avalon6
---

The Avalon Media System allows different levels of access to be assigned to items during their creation. Assigning access control to items can be useful when items or collections need special handling, either due to sensitive content, privacy concerns, or legal requirements. This user guide will explain the different levels of access control and how they are assigned to an item in Avalon.

## Published vs. Unpublished

The following instructions for setting Access Control and granting Special Access refer specifically to published items. Unpublished items, regardless of their access levels, are viewable only by collection members. Leave items unpublished if their details (metadata, structure, access control, etc.) are not yet finalized.

## Access Control Levels

Access to specific items is set manually when items are created.

{% include image.html file="doc_images/access_control.png" alt="access control options" %}

* _Available to the general public_: anyone can view this item, even if they are not logged in as a user.
* _Logged in users only_: only logged-in users may view this item. The item will also not display in search results to the general public.
* _Collection staff only_: only logged-in collection staff may view this item, which includes Managers, Editors, and Depositors.

Additionally, "Hide this item from search results" can be used to make an item available via URL only, and the item will not appear using browse or search. This can be a useful option if the person to whom access is being granted does not have a username or account with Avalon. The item will still be available to the general public (no login required), but access will only be available through a URL.

## Special Access

Beyond the basic access control levels defined above, special access can be given to individual users, specific groups of users, and certain IP addresses or range of IP addresses.

{% include image.html file="doc_images/special_access.png" alt="special access controls" %}

* _Avalon User_: access to an item can be limited to individual users. Enter the username(s) to grant access to the item.
* _Avalon Group_: access to an item can be limited to a pre-defined group of users, e.g. members of a class or department. Select the pre-defined group from the drop-down menu to grant access to the item. If a group needs to be added to the list, contact your Avalon group manager or system administrator.
* _External Group_: access to an item can be limited to groups defined by external services, such as a Learning Management System like Canvas or an LDAP group.
* _IP Address or Range_: access to an item can be limited to an IP address or range of addresses, e.g. a specific computer lab or group of devices.
  * Examples:
    * 255.0.1.10
    * 255.0.1.10/21
    * 255.0.1.10/255.255.255.0
    * 2001:0db8:85a3:0000:0000:8a2e:0370:7334.

Each type of special access can also be further controlled by setting a date range for access. This can be useful if access should be limited to a short time span (e.g. a week or a month) or a pre-determined set of dates (e.g. the duration of a semester or an eight-week course). Leaving these fields empty will set access control to be open-ended.
