---
title: Units and Collections
summary: "Definitions of the default roles in Avalon and their allowable actions."
sidebar: avalon6_sidebar
permalink: avalon6_units_and_collections.html
folder: avalon6
---

## Definitions

* __Authenticated users__ - A user who can access Avalon using a valid identifier and authentication combination supported by your institution. Publicly accessibly items do not require authentication for access.
* __Collection__ - A collection is a grouping of items for administrative and discovery purposes. Items belong to one and only one collection. 
* __Collection Staff__ - Collection staff refers to individuals that have been assigned specific roles for a collection: managers, editors, and depositors. Administrators are also considered collection staff although they are not listed per collection. Collection staff have set permissions to edit, delete, publish items based on their assigned roles; see [Collection Member Roles](avalon6_collection_member_roles) for more information about permissions.
* __File__ - A single media file (i.e. sound recording, moving image) that is part of an item; one or more files can exist for a single item (e.g. 3 mp4 files combined to form an entire movie, 6 wav files together make up the recording of an entire orchestra concert, or a sound file and a moving image file together represent a video with accompanying lecture commentary).
* __Item__ - A single item (media object) accessible through one Avalon page; consists of one or more media files and metadata describing the media file(s).
* __Unit__ - A unit is a grouping of collections for administrative and discovery purposes. Usually, a unit will map to an administrative unit. Collections belong to one and only one unit. A collection's unit is just a label: there are no privileges associated with units.

## Creating Units

In Avalon, Units are used to define ownership and responsibility of collections and their items. Each collection must belong to a unit and collections can belong to only one unit. Each item within a collection can be discovered using Avalon's search bar or browsing the Unit facet.

Only administrators may create or update units; to do so, an administrator will need to update the unit configuration file. Please contact an administrator for assistance (see Managing Units).

## Creating a Collection

Only managers may create, delete, or set default access controls for a collection. Please request to be added to the Manager group by an Avalon administrator.

{% include note.html content="Manager-level access will not automatically provide access to view or edit other collections within a unit. To gain access to other collections in a unit, an administrator or manager for those other collections will need to assign membership in a Collection Staff role (manager, editor, or depositor)." %}

To create a collection:

1. Log in to Avalon.
2. Click Manage Content.
3. Click Create Collection.
4. An inset window will display the New Collection form. Enter a Name and Description for the collection and select the Unit to contain the collection from the drop-down menu. If the desired Unit does not appear in the drop-down list, contact an administrator to add the Unit to Avalon.
5. Click Create Collection.
6. The creator of the new collection will automatically be assigned as Manager.

## Assigning/Removing Collection Members

Once a collection has been created, managers and editors may assign roles in that collection. Managers can assign both editors and depositors, while editors can only assign depositors.

1. Log in to Avalon.
2. Click Manage Content.
3. Click the collection to be edited.
4. Under Assign Staff Roles, add email addresses under Managers, Editors, or Depositors to assign roles to those users. There is no limit to the number of email addresses listed under each role. 
5. Click Add.
6. To remove Collection Staff from a role, click on the "X" following the email address.
   
{% include warning.html content="Each collection must have at least one manager. Attempting to delete the only listed manager will generate an error message and Avalon will prevent that deletion from occurring. Collections do not require editors or depositors." %}

## Editing a Collection

ONly managers and editors may edit a collection.

1. Log in to Avalon.
2. Click Manage Content.
3. Click the collection to be edited.
4. Click Edit Collection Info.
5. Edit the Name, Description, and/or Unit on the Edit Collection Info form.
6. Click the Update Collection button on the Edit Collection form.

## Deleting a Collection

Avalon does not allow deletion of a collection's contents in a single procedure. The content in a collection must first be moved to a different collection. If items need to be deleted from Avalon, each item must be deleted at the item level. Collections that do not contain any items can be deleted without any additional steps. 

Only managers may delete a collection.

1. Log in to Avalon.
2. Click Manage Content.
3. Click Delete next to the collection to be deleted.
   1. Avalon will ask for confirmation before the collection may be deleted.
   2. Select another collection from the drop-down menu into which any remaining items will be moved. If there are no other collections to use, the collection may not be deleted. 
5. Click "Yes, I am Sure" to delete the collection.

{% include links.html %}