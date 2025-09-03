### Updated `date_time.md`

(start_span)This version adds timezone support to the `DateTime` module, a crucial feature for real-world applications.

```markdown
# Date & Time Module

The Zexus `DateTime` module provides a standard way to work with dates, times, and durations.

## Creating a DateTime Object

```zexus
# Get the current date and time in UTC
let now = DateTime.now()

# Create a specific date, assumed to be in the local timezone unless specified
let specificDate = DateTime.new(year: 2025, month: 7, day: 28)

# Create a date and time with an explicit timezone
let tokyoTime = DateTime.new(year: 2025, hour: 10, timezone: "Asia/Tokyo")
```

Functions and Properties
| Name | Purpose | Example |
|---|---|---|
| .year, .month, .day | Gets a specific component of the date. | let year = specificDate.year |
| .hour, .minute, .second | Gets a specific component of the time. | let hour = specificTime.hour |
| .format(as: ...) | Formats the date into a human-readable text string. | now.format(as: "YYYY-MM-DD") |
| .to_timezone(tz) | [cite_start]Converts the DateTime object to a different timezone. [cite: 36] | let localTime = tokyoTime.to_timezone("local") |
| (date1 - date2) | Subtracting dates creates a Duration object. | let timePassed = DateTime.now() - specificDate |
Example Usage
let eventDate = DateTime.new(year: 2026, month: 1, day: 1, hour: 12, timezone: "America/New_York")
let today = DateTime.now()

```zexus
# Convert the event time to the user's local timezone
let eventLocal = eventDate.to_timezone("local")

print "The event is on: {eventLocal.format(as: "Day, Month DD, YYYY at h:mm a")}"