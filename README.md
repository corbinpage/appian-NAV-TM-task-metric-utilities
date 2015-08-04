# NAV_TM Task Metric Utilities
Provides beautiful Task Reports on all Appian tasks in the system without changing any existing applications or in-flight process instances!

## Overview
The NAV_TM Task Metric utilities app is an Appian application that sits on top of existing applications and collects metrics on all tasks in the system. Beautiful, dynamic task reports are included with the app so you can be up and running in minutes without touching any SAIL yourself! Custom task reports and extensions can be built on top of the app to incorporate existing business logic into reports for managers and executives. All task metrics are gathered without changing any existing applications or altering process archival settings and are stored safely in an RDBMS of your choosing for easy retrieval.

## Screenshots

## ToDo:
-Add a Feed post after successful/unsuccessful updates
-Validate that createdAt date is correct
-Truncate text at 255 characters

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
5. You're done! Check out your 'Historical Task Metrics Report' from the Reports tab!

### Dependencies
* Tested with Appian 7.8, 7.9
* Plugins required:
  * [People Functions - Plug-in](https://forum.appian.com/suite/tempo/records/type/components/item/i0BCLGOdlMUpdGVqT-RV7oRg74uEGJO7MQ8lm4tmJLMp94GacLswVsmKlY5dOs/view/summary)
  * [Appian Common Objects Release 2 Rules and Constants](https://forum.appian.com/suite/rest/a/content/latest/ioBWsQdLlzKy55h821pegJS_aao_bClfn6kaA2885s8CkmBit_JcaRqqZM/o)

### Constraints
* Database 
  * Process and task names and descriptions will be truncated to 255 characters.
    * The truncation can be avoided by altering the NAV_TM_TaskMetric CDT and revising the NAV_TM_TEXT_COLUMN_MAX_CHARACTERS constant.
  * As task metrics are collected over time, the database table NAV_TM_TaskMetric will need to be tuned for increased performance.
* Task Reports
  * Approximately 10,000-20,000 task metrics are collected at a time.
  * It's recommended that the Timer in the 'NAV_TM Save Task Metrics' process model be set to run once a day outside of normal business hours but may be adjusted.



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
  * NAV_TM_TaskMetric - CDT to store Task Metric data that is saved to the database.
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
