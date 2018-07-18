---
title: Units and Collections
summary: "Definitions of the default roles in Avalon and their allowable actions."
sidebar: avalon6_sidebar
permalink: avalon6_units_and_collections.html
folder: avalon6/administration
---

## Definitions

Authenticated User
: {{site.data.definitions.authenticated_user}}

Collection
: {{site.data.definitions.collection}}

Collection Staff
: {{site.data.definitions.collection_staff}}

Item
: {{site.data.definitions.item}}

Unit
: {{site.data.definitions.unit}}

## Working with Units

In Avalon, Units are used to define ownership and responsibility of Collections and their Items. Each Collection must belong to one and only one Unit. Units have no associated privileges.

Only Administrators may create or update Units; to do so, an Administrator will need to update the unit configuration file. Please contact an Administrator for assistance.

## Working with Collections

### Creating a Collection

Only Managers may create, delete, or set default access controls for a Collection. Please request to be added to the Manager group by an Avalon Administrator.

{{site.data.alerts.note}}
Manager-level access will not automatically provide access to view or edit other Collections within a Unit. To gain access to other Collections in a Unit, an Administrator or Manager for those Collections will need to assign membership in a Collection Staff role (Manager, Editor, or Depositor).
{{site.data.alerts.end}}

To create a Collection:

1. Select Manage Content.
2. Click Create Collection.
3. An inset window will display the New Collection form. Enter a Name and Description for the Collection and select the Unit to contain the Collection from the drop-down menu. If the desired Unit does not appear in the drop-down list, contact an Administrator to add the Unit to Avalon.
4. Click Create Collection.
5. The creator of the new Collection will automatically be assigned as Manager.

### Assigning/Removing Collection Members

Once a Collection has been created, Managers and Editors may assign roles in that Collection. Managers can assign both Editors and Depositors, while Editors can only assign Depositors.

1. Select Manage Content.
2. Click the Collection to be edited.
3. Under Assign Staff Roles, add email addresses under Managers, Editors, or Depositors to assign roles. There is no limit to the number of email addresses listed under each role. 
4. Click Add.
5. To remove Collection Staff from a role, click on the "X" following the email address.
   
{{site.data.alerts.warning}}
Each Collection must have at least one Manager. Attempting to delete the only listed Manager will generate an error message and Avalon will prevent the deletion.
{{site.data.alerts.end}}

### Editing a Collection

Only Managers and Editors may edit a Collection.

1. Select Manage Content.
2. Click the Collection to be edited.
3. Click Edit Collection Info.
4. Edit the Name, Description, and/or Unit on the Edit Collection Info form.
5. Click the Update Collection button on the Edit Collection form.

### Deleting a Collection

Avalon does not allow deletion of a Collection's contents in a single procedure. The content in a Collection must first be moved to a different Collection. If Items need to be deleted from Avalon, each Item must be deleted at the Item level. Collections that do not contain any Items can be deleted without any additional steps. 

Only Managers may delete a Collection.

1. Select Manage Content.
2. Click Delete next to the Collection to be deleted.
   1. Avalon will ask for confirmation before the Collection may be deleted.
   2. Select another Collection from the drop-down menu into which any remaining items will be moved. If there are no other Collections to use, the Collection may not be deleted. 
3. Click "Yes, I am Sure" to delete the Collection.

{% include links.html %}