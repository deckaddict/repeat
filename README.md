# repeat
Repeat your schedule on android devices.

Script to filter out tasks from task definition files and generate notifications.

Dependencies:
Termux
Termux-api
python
PyYAML

Tasks are configured in .yml files in /sdcard/repeat/
All .yml files in that directory will be parsed.

Any top level element in the yml file is a task.
Tasks can have the attribute "when" to define which date it is valid for.
The when clause shall be a python expression that is evaluated.
Pre-defined variables to use are:
- y: year
- m: month
- w: week
- doy: day of year
- dom: day of month
- dow: day of week

Example:
```
CleanWindows:
  when: w%26 == 13 and dow == 6
```

This will remind you to clean your windows on the sunday of week 13 and week 39 every year.

When fields are sanitized with a naive logic that prevents certain characters.
For example, '.' and '\\' are removed.

To have repeat being run daily by the termux-job-scheduler and termux:boot.
