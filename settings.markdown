---
title: Settings
layout: default
nav_order: 4
---

# Settings Pages

CC-PLUS operates using three separate entities:
* Users
* Providers
* Institutions

Institutions are further described by 
* Groups
* Types

Each of these entities need to be set-up in order to use the system. All of the controls for setting up and managing these entities are available under the “Settings” option in the main navigation menu. 

Although they are listed as above in the drop-down, when initially setting up the system, Providers must be set up first, then institutions, then users. Instructions for setting up all of these using the bulk upload option are found in [Process for initial ingest of settings].

## Users
You can create user accounts for those who will be able to view and create reports in CC-PLUS. User roles are as follows:

* Admin: can create and manage settings for all users, institutions, and providers
* Manager: can manage settings for their own institutions and can create and manage users within their institution
* User: can view statistics for their own institution
* Viewer: can view statistics for all institutions

Roles other than Admin are meant to be used in combination. So Managers must also be either users or viewers in order to both see reports and manage settings. If you have a number of users you would like to add at once, See [Process for initial ingest settings], under Part Four: User Accounts.

The main user settings page lists all the active and inactive users of the system. Each has a User Name, Institution affiliation, Status of Active or Inactive, Email, Roles, and the date of the last login.

[hold for image]

New users can be added in bulk through the import function described in the above mentioned document, or one at a time using the “Create A User” button.

The box that will pop-up when that option is used asks for the user name and email and a password. You must remember the initial password you create and share it with the user. Ask them to change the password upon login.

You must also assign the user to an existing institution and roles. These will be used to determine what data the user has access to. The default for a new user is to be set to active, although you can choose to create an inactive user if you would like.

[hold for image]

If any information for the user changes, it can be edited by an Admin account, or a Manager account (for Managers and Users only). If a user forgets or loses their password, the password can be updated by the Admin or Manager.

## Providers

“Providers” is the term CC-PLUS uses for an entity supplying data through a COUNTER report retrieved via a SUSHI request. These may be vendors, platforms, publishers etc.

The list of providers includes the provider name, it’s status as active or inactive, the institutions that can harvest from this provider, and the day of the month data is harvested.

[hold for image]

New users can be added in bulk through the import function described in [Process for initial ingest of settings], or one at a time using the “Create A Provider” button.

[hold for image]

New providers must be given a name and a URL for the SUSHI service. The institution drop-down indicates which institutions may connect to that provider. To actually initiate harvesting, we will later need to add credentials. The default is to make the provider available to the entire consortium.

You may also choose a day of the month that automated harvests will occur. The default is set to 15.

You must choose which of the four types of COUNTER reports to harvest from the provider. CC-PLUS will harvest full master reports, which can later be customized to correspond to the various COUNTER-determined views. The report types are:
* Title Reports (TR)
* Platform Reports (PR)
* Database Reports (DR)
* Item Reports (IR)

Finally, the provider must have a status. The default is for the provider to be active. Only active providers will show up in options to harvest reports. Once a provider is created and data is stored in the database, they cannot be deleted from the system (because data exists). If you no longer want to harvest data from that provider, you can then make them “inactive.”

If you click the name of a provider, you will be taken to a screen that shows more information about the provider:

[hold for image]

At the top of the page are the basic provider information created when you add them to the system. Underneath this is a collapsed list of recent harvests that have been made to this provider. Clicking the down arrow at the end of the line will open up the list. This will aggregate harvests across multiple institutions if you have permission to view their data.

[hold for image]

More information about the harvest log is available in [[Harvesting Reports].

Under the harvest activity is the list of institutions that have been connected to the provider for harvesting. A new connection can be made by selecting an institution from the drop-down list:

[hold for image]

Once the institution is chosen a form will open up to add the customer ID, requestor ID, and API key credentials. Clicking connect will save the connection, and automated harvesting will begin on the next harvest date.

In the list of existing connections, you can either delete the credentials, or open and edit them by clicking “Settings & Harvests”

[hold for image]

The resulting page will list the credentials, which are editable, and a list of the recent harvests for this specific provider and institution.

## Institutions

Institutions are the last entities involved in the CC-PLUS system. 

As with the other two entities, instructions to add institutions in bulk are found in [Process for initial ingest of settings]. They can be added individually by clicking “Create an Institution.”

[hold for image]

Institutions are described with a name, and type (which will be described further later), and whether or not they are active or inactive. Like Providers, if data exists for the system it cannot be deleted and must be made “inactive” if you no longer wish to harvest data.

Institutions can further be optionally described with the number of FTE, membership in a group (also described further later), and an open note field.

When clicking on a name in the Institution list, a page similar to that of the provider opens.

[hold for image]

Again, the main details are listed at the top of the page and are editable. Additionally, the list of user accounts affiliated with the institution are listed and new user accounts can be added from this screen.

Similar to the Providers page, the Institution page also have a list of recent activity, and the credentials for various providers. New credentials can be set up by choosing the Provider from the drop-down list and adding the credentials as was done in the Provider example above.

## Institution Groups

CC-PLUS allows for the creation of groups of institutions for quick access to data for multiple institutions. Groups can be composed of any combination of institutions, and institutions may be part of multiple groups. Creating a group can speed up the process of creating custom reports or doing harvests for data.

[hold for image]

The groups list is very simple, with just name and buttons to edit or delete. Groups can be created or edited in bulk (instructions TBD). Creating a new group is a two-part process. First click the button to “Create a New Group.” A pop-up box will ask for the name of the new group.

[hold for image]

Once the name is saved, you will return to the list of groups. From there, you can choose to “Edit” the new group. Institutions can then be added or removed to the group in the next window.

[hold for image]

Institution Types
CC-PLUS is set up to require all institutions to be described using a single type descriptor. If you do not wish to use this feature, you can just assign all institutions to the default type 1 “(not assigned”.

The application is set up with the Carnegie Classification codes as a default list of types.

[hold for image]

These can be renamed or deleted on this screen. Alternatively, you can simply upload a new list of your own using the “Import Types” button (instructions TBD).



