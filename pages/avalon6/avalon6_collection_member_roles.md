---
title: Collection Member Roles
summary: "Definitions of the default roles in Avalon and their allowable actions."
sidebar: avalon6_sidebar
permalink: avalon6_collection_member_roles.html
folder: avalon6
---

## Role Definitions

Avalon has 4 default roles:

* __Administrator__ - Administrators are a select few who have responsibility for providing an Avalon-based service. The Administrators assign people to the Manager role and maintain the list of Units. Administrators are the only ones who can see and modify Items in any collection. This role is typically limited to system administrators and administrative unit managers. Administrators do not need to be added to individual Collections since they can view, edit, and delete any Items in Avalon. 
* __Manager__ - Managers are those within a given Unit who have overall accountability for building Collections within Avalon. Managers create Collections and assign Editor and Depositor roles for those Collections. They set the default access controls for Items added to a Collection and intervene when a published Item needs to be revised or deleted. 
* __Editor__ - Editors have supervisory responsibility for the ingest and description process (i.e. collection building). They can assign Depositor roles, change the name or description of a Collection, and modify access controls for individual Items in a collection.
* __Depositor__ - Depositors add and describe media into Collections. They can publish Items but not unpublish. They can only modify or delete unpublished Items.

Permissions are hierarchical (i.e. an Editor can do anything a Depositor can do, a Manager can do anything Editors and Depositors can do, an Administrator can do anything).

## Role Permissions

|--------------------------------------|---------------|---------|--------|-----------|
| Action                               | Administrator | Manager | Editor | Depositor |
|:-------------------------------------|:-------------:|:-------:|:------:|:---------:|
| Create administrative Units          | X             |         |        |           |
| View all Collections                 | X             |         |        |           |
| Create Collections                   | X             | X       |        |           |
| Edit Collection information          | X             | X       | X      |           |
| Set default Collection access control| X             | X       |        |           |
| Delete Collections                   | X             | X       |        |           |
| Manage Groups                        | X             |         |        |           |
| Add/remove Managers                  | X             |         |        |           |
| Add/remove Editors                   | X             | X       |        |           |
| Add/remove Depositors                | X             | X       | X      |           |
| Add Items                            | X             | X       | X      | X         |
| Set Item access control              | X             | X       | X      |           |
| Add metadata                         | X             | X       | X      | X         |
| Publish Items                        | X             | X       | X      | X         |
| Edit published Items                 | X             | X       |        |           |
| Delete published Items               | X             | X       |        |           |
| Unpublish Items                      | X             | X       |        |           |
| Edit unpublished Items               | X             | X       | X      | X         |
| Delete unpublished Items             | X             | X       | X      | X         |
| Move Items to other Collections      | X             | X       |        |           |
| Batch ingest                         | X             | X       | X      | X         |
| View administrative metadata         | X             | X       | X      | X         |
|--------------------------------------|---------------|---------|--------|-----------|

{% include links.html %}
