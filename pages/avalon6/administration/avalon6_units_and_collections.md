---
title: Units and Collections
summary: "Definitions of the default roles in Avalon and their allowable actions."
sidebar: avalon6_sidebar
permalink: avalon6_units_and_collections.html
folder: avalon6/administration
---

## Definitions

Collection
: {{site.data.definitions.collection}}

Collection Staff
: {{site.data.definitions.collection_staff}}

Unit
: {{site.data.definitions.unit}}

## Working with Units

Units define ownership and responsibility for collections, as each collection must belong to a single unit. Units have no associated privileges on their own, but are often mapped to physical administrative units (i.e. a specific library or archive).

Only administrators may create or update units; the list of units for an Avalon instance is maintained in the unit configuration file, accessible to administrators only.

## Working with Collections

Only managers may create collections, delete collections, or set default access controls for a collection.

Additionally, manager-level access does not provide access to view/edit another manager's collections within the unit. To gain access, the other manager will need to assign membership in a collection staff role.

### Creating a Collection

1. Go to __Manage Content__.
2. Select __Create Collection__.
3. Enter a name and description, and select a unit for the collection.
4. Select __Create Collection__.

A collection's creator is automatically assigned as manager.

### Assigning/Removing Collection Staff Members

To assign collection staff after creating a collection:

1. Go to __Manage Content__.
2. Select a collection.
3. Under __Assign Staff Roles__, specify a username/email address for the appropriate role.
4. Select __Add__.

To remove collection staff:

* Select the __X__ following the username/email address.
   
{{site.data.alerts.danger}}
Each collection must have at least one manager. Attempting to delete the only listed manager generates an error.
{{site.data.alerts.end}}

### Editing a Collection

1. Go to __Manage Content__.
2. Select a collection.
3. Select __Edit Collection Info__.
4. Enter new values for name or description, and/or select a new unit for the collection.
5. Select __Update Collection__.

### Deleting a Collection

{{site.data.alerts.danger}}
Collections and their items cannot be deleted in a single procedure. Before deleting a collection, the items in the collection must be moved to a different collection (see Step 3 below), or deleted at the item level.
{{site.data.alerts.end}} 

1. Go to __Manage Content__.
2. Select __Delete__ for a collection.
3. If the collection still contains items, select another collection to host the items. 
4. Select __Yes, I am Sure__ to delete the collection.

{% include links.html %}