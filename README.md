# Lock My Phone
Official Bug Tracker and Feature Request-Forum for the Android App **Lock My Phone**

You can get the app [here](https://play.google.com/store/apps/details?id=tomka.lockmyphone) on Google Play (500k+ downloads 🎉).

# Getting Lock My Phone to work with [Automate](https://play.google.com/store/apps/details?id=com.llamalab.automate) (and, by extension, [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm))

Automate is one of my favorite apps because it allows me to control my environment better. This [makes me happy](https://www.joelonsoftware.com/2000/04/10/controlling-your-environment-makes-you-happy/).

## Overview

Lock My Phone (LMP) can interact with Automate in three ways:

* LMP will notify Automate via broadcast every time the lock status of the phone changes.
* Automate can demand a list of all existing locks from LMP (via broadcast). LMP will then broadcast that list back to Automate.
* 🆕 Enable or disable individual locks (works with one time and recurrring locks).

## 1. Receiving status updates from LMP in Automate

Example use case: Use this to automatically enable Do Not Disturb-mode when a lock period begins.

There are four possible states that LMP will broadcast to Automate:

- Lock period inactive
- Lock period active, inside lock area
- Lock period active, outside lock area
- Lock period active, lock everywhere

To receive status updates from LMP in Automate you have to enable receiving broadcasts. Here is a flow that does just that (4 blocks):

[Flow "Receiving lock status updates"](https://www.thomaskahn.de/lockmyphone/download.php?action=download&file=LMP_Receive_Status_Updates_for_Locks.flo)

## 2. Receive a list of all currently enabled recurring locks

Example use case: Send daily email reports about your locks to a friend whom you promised you would use Lock My Phone regularly while you're preparing for an exam.

[Flow "Receiving the lock list"](https://github.com/tomkahn/lockmyphone_public/raw/9c1755aad2ab935aaf567fda21efd05397f601bb/LMP_Automate_flow/LMP_get_list_of_all_enabled_locks_with_last_time_activated.flo) (The fastest way)

[Flow "Sending email reports about your enabled locks"](https://www.thomaskahn.de/lockmyphone/download.php?action=download&file=LMP_Daily_E-Mail-Reports.flo) (advanced example): This flow also shows you how to loop through the JSON data that LMP sends to Automate.

## 3. Receive a list of all created locks

Example use case: Get a complete list of all locks you have created in Lock My Phone (both enabled and disabled) for backup, synchronization, analytics, or custom automation.

[Flow "Receiving the list of all created locks"](https://github.com/tomkahn/lockmyphone_public/raw/refs/heads/master/LMP_Automate_flow/LMP_Get_list_of_all_created_locks.flo) (Returns all created locks regardless of their current state)

## 🆕 4. Enable or disable a lock

First you must get the ID of the lock you want to enable or disable. Each lock has a unique ID (a number, for example 3) which you can find in the menu of the lock on the bottom right:

[🖼 Where do I find the ID?](https://e.pcloud.link/publink/show?code=XZVlc1Zvq8lHUxA6bLBzEgplzglc71fpgEk)

To start a lock [broadcast "START 3"](https://e.pcloud.link/publink/show?code=XZ9lc1Z8EgIYgLGFJLo0K3wyVGYxfUpSXaV) (if 3 is the ID of the lock you want to activate) to Lock My Phone. Here is a flow that does that:

[⏬ Flow "Starting a lock period from Automate"]([https://www.thomaskahn.de/lockmyphone/download.php?action=download&file=LMP_Start_locks.flo](https://e.pcloud.link/publink/show?code=XZYlc1ZLhpE0FiYL5jwdvjprvvIT7mAAOnV)https://e.pcloud.link/publink/show?code=XZYlc1ZLhpE0FiYL5jwdvjprvvIT7mAAOnV) (The fastest way)

☝ Please note: Under Android 13 and up starting a lock from outside of Lock My Phone is only possible when Lock My Phone is already running in the background. To get LMP running in the background you must have at least one recurring lock period enabled. It can be a very short one that only locks your phone for 1 minute on 1 specific day only.

To stop a lock broadcast "STOP 3" (if 3 is the ID of the lock you want to activate) to Lock My Phone.
