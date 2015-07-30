# NAV_TM Task Metric Utilities
Provides beautiful Task Reports on all Appian tasks in the system without changing any existing applications or adjusting archival settings.

## Overview
The NAV_TM Task Metric utilities app is an Appian application that sits on top of existing applications and collects metrics on all tasks in the system, so they can be used in reports straight from an RDBMS even after process instances are archived. Without changing any existing applications or altering archival settings, you can release beautiful task reports to your executives or managers within a matter of minutes. 

## Screenshots

## ToDo:
-Add Button for filter
-Expand column size of text in the database
-Add a Feed post after successful/unsuccessful updates
-Add the different fields collected
* Appian market
  * App Name: NAV_TM Task Metric Utilities
  * Target Industry: All
  * Short description: Above
  * Detailed Description: Above
  * Screeshots (min 4 , max 8) need
  * Primary contact info
  * Sales Info
  * Customer quotes
  * Demo video

## Install
1. Import the 'NAV_TM Task Metric Utilities' application.
2. Review the NAV_TM Data Store, select the appropriate data source, and publish the data store.
3. Set the Timer on the 'NAV_TM Save Task Metrics' process model.
4. Run the process at least once.
5. You're done! Check out your 'Completed Task Metrics Report' from the Reports tab!

### Dependencies
* Tested with Appian 7.8, 7.9
* Plugins required:
  * [People Functions - Plug-in](https://forum.appian.com/suite/tempo/records/type/components/item/i0BCLGOdlMUpdGVqT-RV7oRg74uEGJO7MQ8lm4tmJLMp94GacLswVsmKlY5dOs/view/summary)
  * [Appian Common Objects Release 2 Rules and Constants](https://forum.appian.com/suite/rest/a/content/latest/ioBWsQdLlzKy55h821pegJS_aao_bClfn6kaA2885s8CkmBit_JcaRqqZM/o)

### Caveats
1. Database text alterations
2. Greater than ~10000 tasks, need to alter
3. Database tuning



## Components
### Task Metric Reports
	-Who's completing the most tasks?
	-Who takes the longest to complete? In time and workday time?
	-Which tasks take the longest time? The shortest? All with drilldowns.


### Saving Task Metrics
* NAV_TM Save Task Metrics Process Model - Batch process that runs periodically to query the system for all tasks and saves them to the database.
* Portal Reports
  * NAV_TM All Tasks for Groups - Used to get all tasks assigned to groups.
  * NAV_TM All Tasks for Users - Used to get all tasks assigned to or accepted by users. 
* Groups
  * NAV_TM Administrators - Users in this group have administrator access of the NAV_TM app.
  * NAV_TM All Groups and Users - Users and groups that are members of this group will have their task metrics saved. By default it includes all users and groups in the system via a group membership rule.
  * NAV_TM Historical Task Metrics Report Viewers - Users in this group can view the Completed Tasks Report from the Reports tab.
* Data
  * NAV_TM_TaskMetric - Task Metrics CDT that is saved to the database.
  * NAV_TM Data Store - Data Store used for the NAV_TM app. You'll need to point the data store to a schema.

## Future Development
* Create reports for Active Tasks
* Generic task reassignment action
* Include room for custom fields
* Include some kind of work around for reporting on "wizard" tasks
* Anything else? You tell [me](mailto:corbin@nav-labs.com)!

## License
[The MIT License (MIT)](/LICENSE)

## Issues, Troubleshooting, & Feedback
Feel free to reach out to [Corbin Page](mailto:corbin@nav-labs.com) if you run into any issues, have feedback, or think of any feature requests. I plan to update this app often and would love to incorporate anything you need!
