# Punch Starting Points
Changes to be made to the employee API are the following:

allow for proper authentication associated with the accounts - do not let cross account access be able to modify other paying customer and businesses employees. Manage this through secure Http Only cookies
Visibility and access is restricted to each account holder in their own right - they do not bleed into other sectors within the application.
re update these HttpOnly cookies on tier selection - do this through the server side.
WORK ON APIS FIRST, Fuckkkk THE FRONT END

> Employee APIs (building employee roster)
> Punch APIs (Allow for employees to commit punch actions)

# Tier ONE

Simple punch clock features, standalone, and non dependent on scheduling, zoning, etc.

GET all employees

Once an employee is selected, update fields with punch clock timings. If this is the first punch of the day, store within the employee's record. If it is the LAST [second], calculate the difference of time, and store within the overall account's Timesheet collection.

How should this work?
1. Query Employee
2. Call API endpoint (Update)
3. Validity checks (If this is the last punch, calculate the hour difference.)

# Punch Tier 1 API

The intial punch function for the base tier should return the following:
- current day and hour.
- UNIX timestamp for punch recording
- time difference between two punches