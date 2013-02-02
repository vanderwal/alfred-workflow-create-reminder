Workflow for setting reminders in Alfred version 2
===============

* by Michelle L. Gill, 02/02/2013
* Applescript in workflow inspired by [Jayphen](https://gist.github.com/3187630)
* The Applescript which runs this workflow is available [here](https://gist.github.com/3813222)

Changes to original workflow (posted in Alfred forums)
===============

## 02/01/2013

* Fixed an issue with setting the time when the hour is 12 and AM/PM (12-hour clock) is used
* Removed the ability to set seconds for the time since Reminders doesn't recognize them

## 02/02/2013

* Fixed a regression in setting the date when only the hour is present
* Added the ability to return information from the created reminder as a string for error checking.
* This returned string is used to post a notification in the workflow.

Notes on valid reminders
===============

* Order of the text must be "title #note $list @date time" but note
* List is optional if a default is set within the script
* Time must be included, but date can be omitted and is assumed to be today
* Time can be in 12- or 24-hour format, and 24-hour format is assumed if am/pm are absent
* Time can be either just the hour or colon separated (hour:minute)
* Numerical dates are listed as month/day/year and year isn't required
* Relative dates such as "Today" and "Tomorrow" can be used, as well as days of the week
* Relative dates are case instensitive and can be abbreviated, i.e. "mon" for "Monday"
* If the day of the week is entered as "Sunday" and today is Sunday, 7 days from today will be returned
* "Next" can be added to relative dates return an additional seven days from the appropriate day of the week

Examples of valid reminders
===============

	Buy Milk #note about milk $Personal @10/7/2012 5:00 PM
	Buy Milk #note about Milk @10/7/2012 5:00 PM
	Buy Milk $Personal @10/7/2012 5:00PM
	Buy Milk @10/7/2012 5:00 PM
	Buy Milk @10/7/12 5:00pm
	Buy Milk @10/7/12 5pm
	Buy Milk @10/7 5pm
	Buy Milk @Tomorrow 5pm
	Buy Milk @tomorrow 5pm
	Buy Milk @tom 5pm
	Buy Milk @Sunday 5pm        this returns 10/14/2012 if today is Sunday, 10/7/2012
	Buy Milk @sunday 5pm        this returns 10/14/2012 if today is Sunday, 10/7/2012
	Buy Milk @sun 5pm           this returns 10/14/2012 if today is Sunday, 10/7/2012
	Buy Milk @Next Sunday 5pm   this returns 10/21/2012 if today is Sunday, 10/7/2012
	Buy Milk @next sun 5pm      this returns 10/21/2012 if today is Sunday, 10/7/2012
	Buy Milk @today 17          this assumes time is in 24-hour format, i.e. 5pm
	Buy Milk @today 5           this also assumes time is in 24-hour format, i.e. 5am
	Buy Milk @5pm               this also assumes time is in 12-hour format
	Buy Milk @5                 this also assumes time is in 24-hour format, i.e. 5am