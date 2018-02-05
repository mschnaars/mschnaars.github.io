---
title: Collection Member Roles
summary: "Definitions of the default roles in Avalon and their allowable actions."
sidebar: avalon6_sidebar
permalink: avalon6_collection_member_roles.html
folder: avalon6
---

## Role Definitions

Avalon has 4 default roles:

* __Administrator__ - Administrators are a select few who have responsibility for providing an Avalon-based service. The administrators assign people to the manager role and maintain the list of units. Administrators are the only ones who can see and modify items in any collection. This role is typically limited to system administrators and administrative unit managers. Administrators do not need to be added to individual collections since they can view, edit, and delete any items in Avalon. 
* __Manager__ - Managers are those within a given unit who have overall accountability for the collection building within Avalon. Managers create collections and assign editor and depositor roles for those collections. They set the default access controls for items added to a collection and they also step in when a published item needs to be revised or deleted. 
* __Editor__ - Editors have supervisory responsibility for the ingest and description process (i.e. collection building). They can assign depositor roles, change the name or description of a collection, and modify access controls for individual items in a collection.
* __Depositor__ - Depositors add media to a collection and describe it with metadata. They can publish items but not unpublish. They can only modify or delete unpublished items.

Permissions are also inherited (i.e. an editor can do anything a depositor can do, a manager can do anything editors and depositors can do, an administrator can do anything).

## Role Permissions

|--------------------------------------|---------------|---------|--------|-----------|
| Action                               | Administrator | Manager | Editor | Depositor |
|:-------------------------------------|:-------------:|:-------:|:------:|:---------:|
| Create administrative units          | X             |         |        |           |
| View all collections                 | X             |         |        |           |
| Create collections                   | X             | X       |        |           |
| Edit collection information          | X             | X       | X      |           |
| Set default collection access control| X             | X       |        |           |
| Delete collections                   | X             | X       |        |           |
| Manage groups                        | X             |         |        |           |
| Add/remo^e managers                  | X             |         |        |           |
| Add/remove editors                   | X             | X       |        |           |
| Add/remove depositors                | X             | X       | X      |           |
| Add items                            | X             | X       | X      | X         |
| Set item access control              | X             | X       | X      |           |
| Add metadata                         | X             | X       | X      | X         |
| Publish items                        | X             | X       | X      | X         |
| Edit published items                 | X             | X       |        |           |
| Delete published items               | X             | X       |        |           |
| Unpublish items                      | X             | X       |        |           |
| Edit unpublished items               | X             | X       | X      | X         |
| Delete unpublished items             | X             | X       | X      | X         |
| Move items to other collections      | X             | X       |        |           |
| Batch ingest                         | X             | X       | X      | X         |
| View administrati^e metadata         | X             | X       | X      | X         |
|--------------------------------------|---------------|---------|--------|-----------|

{% include links.html %}
