# Office365
<b>Office365 Migration Tools - Office 365 Grouper</b>

Previously Updated: 7/26/2017

<b>Last Updated: 8/9/2017</b>

Desc: Updated per github user base request for additional functionality.

The Office365 Grouper utility is utilized to perform grouping of users by aliases gathered from a combination of Get-Mailbox and Get-MailBoxPermissions, the utility groups mailbox permissions by utilizing the alias attribute as a primary key.
Once the CSV has been loaded into the utility, it is able to loop through the list performing advanced logic to filter the data according to office location and or exemption list via alias.

<b>How does this all work?</b>

Office365 Grouper has 2 Phases of operation,

Phase 1 will iterate through the provided CSV to sort users by office location and or exemption list while building an index for quicker searching and avoiding nested loops in phase 2.

Phase 2 will ignore "S-1-5 sids", "NT AUTHORITY\SELF", "Duplicates", "AccessRights that only equal FullAccess", while the utility matches aliases it extracts the user from the mailbox permission field and then compares against the index created.
This indexing allows for the application to directly locate the users in a very large csv instead of looping I.E. 25,000 x 25,000.
Once the user has been located in the index, it extracts the line item and builds a new CSV that matches the filtered criteria only.
Resulting in the ability to group users by office location and or exemption list.

<b>Changes in this version:</b>

-Fixed issue where duplicates would be included in a migration batch.

-Reduced nested loop functionality by implementing indexing.

-Implemented Exemption List instead of static runtime parameters.

-Implemented Office List instead of static runtime parameters.

-Implemented Progress Bar and Phase Indicator.

-Implemented Failsafe logic for start process, removal of exemptions/office on selected, add of exemption/office on selected.

-Implemented right click context menu for quick add/removal of exemptions and office changes.

-Implemented ability to check if office.ini or exempt.ini has changed since the application loaded the file and prompts to reload.

-Updated Application Icon.

<b>Upcoming changes:</b>

-Ability to filter by more than office and or user alias.

-Dynamic arrays to optimize time it takes to process data.

-Implementing Stop/Pause Button.

-Param Strs so that application can me launched with parameters to script/automate functionality.

If you have any other questions or request for updates, let me know and i will try my best to accomodate.

JadedDeveloper
