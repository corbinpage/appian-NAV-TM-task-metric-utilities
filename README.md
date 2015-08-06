# Task Metric Utilities
Runs in the background to collect TONS of Appian task metrics and provides beautiful Reports without modifying existing applications!

![Overview Images](/images/historical-task-metrics-report-overview.png?raw=true "Overview Images")

## Overview
The NAV_TM Task Metric utilities app is an Appian application that sits on top of existing applications and collects metrics on all tasks in the system. Beautiful, dynamic task reports are included with the app so you can be up and running in minutes without touching any SAIL yourself! 

The app collects a TON of task metrics in the background so that custom reports can be built on top of the dataset as well, incorporating pertinent business logic for your managers and executives! 

All task metrics are gathered without changing any existing applications or altering process archival settings and are stored safely in an RDBMS of your choosing.

## Additional Screenshots

![Clickable Pie Chart](/images/bottleneck-with-pie.png?raw=true "Clickable Pie Chart")

![Reveal grid](/images/bottleneck-with-grid.png?raw=true "Reveal grid")

![Task Metrics Grid](/images/historical-task-metrics-report-grid.png?raw=true "Task Metrics Grid")

## Install
1. Import the 'NAV_TM Task Metric Utilities' application.
2. Review the NAV_TM Data Store, select the appropriate data source, and publish the data store.
3. Set the timer on the 'NAV_TM Save Task Metrics' process model.
4. Run the process at least once.
5. You're done! Check out your 'Historical Task Metrics Report' from the Reports tab!

### Dependencies
* Tested with Appian 7.9+
* Plugins required:
  * [People Functions - Plug-in](https://forum.appian.com/suite/tempo/records/type/components/item/i0BCLGOdlMUpdGVqT-RV7oRg74uEGJO7MQ8lm4tmJLMp94GacLswVsmKlY5dOs/view/summary)
  * [Appian Common Objects Release 2 Rules and Constants](https://forum.appian.com/suite/rest/a/content/latest/ioBWsQdLlzKy55h821pegJS_aao_bClfn6kaA2885s8CkmBit_JcaRqqZM/o)

### Constraints
* Database 
  * Process and task names and descriptions will be truncated at 255 characters.
    * The truncation can be avoided by altering the NAV_TM_TaskMetric CDT and revising the NAV_TM_TEXT_COLUMN_MAX_CHARACTERS constant.
  * As task metrics are collected over time, the database table NAV_TM_TaskMetric will need to be tuned for optimal performance.
* Task Reports
  * Approximately 10,000 task metrics are collected at a time.
  * It's recommended that the timer in the 'NAV_TM Save Task Metrics' process model be set to run once a day outside of normal business hours but may be adjusted.

## Components
### Task Metric Reports
* Number of tasks completed by different individuals (bar chart)
* Most frequently completed tasks (bar chart)
* Task completion duration (pie chart)
* Lag and Work time (stacked bar chart)
* Filters
  * Selected Task
  * Original Assginee(s)
  * Completed (within)
  * Completed By


### Saving Task Metrics
* **NAV_TM Save Task Metrics Process Model** - Batch process that runs periodically to query the system for all tasks and saves them to the database.
* **Groups**
  * *NAV_TM Administrators* - Users in this group have administrator access of the NAV_TM app.
  * *NAV_TM All Groups and Users* - Users and groups that are members of this group will have their task metrics saved. By default it includes all users and groups in the system via a group membership rule.
  * *NAV_TM Historical Task Metrics Report Viewers* - Users in this group can view the Historical Task Metrics Report from the Reports tab.
* **Data**
  * *NAV_TM_TaskMetric* - CDT to store Task metric data that is saved to the database.
  * *NAV_TM Data Store* - Data Store used for the NAV_TM app. You'll need to point the data store to a schema of your choice.

## Future Development
* Reports for Active Tasks
* Additional drilldown reports
* Task reassignment action
* Incorporate "wizard" tasks
* Anything else? You tell [me](mailto:corbin@nav-labs.com)!

## License
[MIT License](/LICENSE)

## Issues, Troubleshooting, & Feedback
Feel free to reach out to [Corbin Page](mailto:corbin@nav-labs.com) if you run into any issues, have feedback, or of any feature requests. I plan to update this app often and would love to incorporate anything you need!
