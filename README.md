# Lock My Phone
Official Bug Tracker and Feature Request-Forum for the Android App **Lock My Phone**

You can find the app here:
https://play.google.com/store/apps/details?id=tomka.lockmyphone

# Getting Lock My Phone to work with [Automate](https://play.google.com/store/apps/details?id=com.llamalab.automate) (and, by extension, [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm))

Automate is one of my favorite apps because it allows me to control my environment better. This actually [does make me happy](https://www.joelonsoftware.com/2000/04/10/controlling-your-environment-makes-you-happy/).

## Overview

Lock My Phone can interact with Automate in two ways:

1. LMP will notify Automate via broadcast every time the lock status of the phone changes.
2. Automate can demand a list of all currently enabled *recurring locks* from LMP (via broadcast). LMP will then broadcast that list back to Automate.

## 1. Receiving status updates from LMP in Automate

Example use case: Use this to automatically enable Do Not Disturb-mode when a lock period begins.

There are four possible states that LMP will broadcast to Automate:

- Lock period inactive
- Lock period active, inside lock area
- Lock period active, outside lock area
- Lock period active, lock everywhere

To receive status updates from LMP in Automate you have to enable receiving broadcasts. Here is a flow that does just that (4 blocks):

[Flow "Receiving lock status updates"](http://www.thomaskahn.de/lockmyphone/download.php?action=download&file=LMP_Receive_Status_Updates_for_Locks.flo)

## 2. Receive a list of all currently enabled recurring locks

Example use case: Send daily email reports about your locks to a friend whom you promised you would use Lock My Phone regularly while you're preparing for an exam.

[Flow "Receiving the lock list"](http://www.thomaskahn.de/lockmyphone/download.php?action=download&file=LMP_Get_list_of_all_enabled_locks.flo) (The fastest way)

[Flow "Sending email reports about your enabled locks"](http://www.thomaskahn.de/lockmyphone/download.php?action=download&file=LMP_Daily_E-Mail-Reports.flo) (advanced example): This flow also shows you how to loop through the JSON data that LMP sends to Automate.
