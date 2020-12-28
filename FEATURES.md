# Features

## Alarm Clock
Turn bedroom lights on at a specified time in order to wake up.

## Away
Critical alerts when away if motion is detected inside. Also turns off all lights and sets thermostat in "eco" mode.

## Backup
Automatically create snapshot each night for backup purposes with copying to NAS for offsite replication.

## Cloud
Very little cloud/internet dependancy.

## Do Not Disturb
Ability to manually suppress alerts if I don't want to be disturbed.

## Emergency
Turn all lights on and strobe color lights when something critical occures.

## Manual
Manual switches and controls in the event things go wrong.

## Sleep
Internal control for when sleeping, so things don't happen in the middle of the night that aren't supposed to.

## States
Implements [Nonbinary Presence Detection] for easy, yet powerful, presence detection.

State | Purpose
--- | ---
home | In "home" zone or been 'just_arrived' or 'just_woke' for a set amount of time.
just_left | Just left the "home" zone.
away | Been 'just_left' or 'out' for a set amount of time.
just_arrived | Just entered the "home" zone.
in_bed | Bedroom door just closed.
sleeping | Been 'in_bed' for a set amount of time.
just_woke | Bedroom door just opened.
out | Out for a short time. Not fully "away".

````
home -> just_left -> away -> just_arrived -> home

home -> in_bed -> sleeping -> just_woke -> home

home -> out -> away -> just_arrived -> home
````

[Nonbinary Presence Detection]: https://philhawthorne.com/making-home-assistants-presence-detection-not-so-binary/
