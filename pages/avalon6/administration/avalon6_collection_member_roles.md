---
title: Collection Member Roles
summary: "Definitions of the default roles in Avalon and their allowable actions."
sidebar: avalon6_sidebar
permalink: avalon6_collection_member_roles.html
folder: avalon6/administration
---

## Role Definitions

__Administrator__
: Administrators are a select few who have responsibility for providing an Avalon-based service. Avalon administrators maintain the list of units and assign users to the manager role; additionally, administrators are the only collection staff members who can see and modify items in any collection. This role is typically limited to system admins and administrative unit managers. Administrators do not need to be added to individual collections since they can view, edit, and delete any items in an Avalon instance. 

__Manager__
: Managers have overall accountability for building collections within a given unit. Managers assign editor/depositor roles, create collections, set default access controls for collections, and intervene when a published item needs revision or removal.

__Editor__
: Editors have supervisory responsibility for item ingest and description (i.e. collection building). They can assign depositor roles, edit basic collection information, and modify access controls for individual items.

__Depositor__
: Depositors have primary responsibility for item ingest and description (i.e. data entry). They can publish items (but not unpublish) and  modify or delete unpublished items.

## Role Permissions

Permissions are hierarchical--editors can perform all depositor tasks, managers can perform editor/depositor tasks, and administrator can perform all tasks.

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
| Add/remove managers                  | X             |         |        |           |
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
| View administrative metadata         | X             | X       | X      | X         |
|--------------------------------------|---------------|---------|--------|-----------|

{% include links.html %}
