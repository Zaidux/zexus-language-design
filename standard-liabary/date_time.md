# Date & Time Module

# Functions and Properties
| Name | Purpose | Example |
|---|---|---|
| .year, .month, .day | Gets a specific component of the date. | let year = specificDate.year # 2025 |
| .hour, .minute, .second | Gets a specific component of the time. | let hour = specificTime.hour # 18 |
| .format(as: ...) | Formats the date into a human-readable text string. | now.format(as: "YYYY-MM-DD") # "2025-07-28" |
| (date1 - date2) | Subtracting dates creates a Duration object. | let timePassed = DateTime.now() - specificDate |
Example Usage
let eventDate = DateTime.new(year: 2026, month: 1, day: 1)
let today = DateTime.now()

let durationUntilEvent = eventDate - today

print "The event is on: {eventDate.format(as: "Day, Month DD, YYYY")}"
print "There are {durationUntilEvent.to_days()} days until the event!"


The Zexus `DateTime` module provides a standard way to work with dates, times, and durations.

## Creating a DateTime Object

```zexus
# Get the current date and time
let now = DateTime.now()

# Create a specific date
let specificDate = DateTime.new(year: 2025, month: 7, day: 28)

# Create a date and time
let specificTime = DateTime.new(year: 2025, month: 7, day: 28, hour: 18, minute: 54)


