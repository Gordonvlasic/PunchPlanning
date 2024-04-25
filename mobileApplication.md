# Mobile Application Planning

The mobile application acts as the terminal where **Employees** will interact. 

## Logic

The mobile application authenticates by login methods. Once authenticated, display a simple UI used for punch, and time of request features. Employees interact with the terminal. Allow to quickly unsend a punch if accidentally submitted.

Depending on the provided authorization token, submit specified API requests.

### Tier 1 Functionality

Tier 1 offers basic punch clock functionality, users will be able to query for themselves, and commit a punch

### Tier 2 Functionality

Tier 2 offers punch clock functionality with scheduling. Employees will still query for themselves, however before punching, the schedule is cross
referenced, checking to see if the employee is scheduled at the correct time. If true, allow punch.

### Tier 3 Functionality

Tier 3 offers Geolocation based work-sites. Users will select themselves, and see the designated jobs, and its location. A pre-defined worksite radius is set, 
the app will ping to make sure it is still within the location every `x` minutes.