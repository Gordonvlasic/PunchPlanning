# Punchhh  Clock

A multi-tier, multi-microservice SaaS solution, targeted at all establishments required of employee time tracking.

## High-Level Rundown

Users will sign up and create a business account on the Punchhh website along with an employee roster, in tandem, creating access to the employee access terminal. (Mobile application)

When initiated, employees will be able to interact with the terminal, punching in and out.

Some punch options are available throughout all tiers:

Break tracking:

    optionally track employee breaks (require additional punches)
    
Late Detection: 

    Flag punches that are "X" past an expected punch time (00 / 30)

Paid/Unpaid breaks:

    enable paid or unpaid breaks for a particular employee

## Punchhh Functionality
All Signup, Setup, and Maintenance within the service is directed through the Website/service. 
After selecting a tier, account creation will then be requested. Detailed about the business will be requested en par to the selected tier. 
Once an establishment is signed up, they will be prompted to create an employee roster. Once again, en par with the selected tier, certain information will be requested.

# Website Architecture
Below find the detailed elements and microservices related to Punchhh

# Database Architecture
Below find the instrinsic associated database structure within the punchh application.

### Registration 
- email
- password
- business name

# System Functions / Microservices 

### Authentication
1. Registration function - allow users to create a new account
2. Login function - allow past users to log back into their existing account

### Employee Roster
1. Intialize buisness roster
2. Add users to existing roster
3. Allow for punch functionality

# Punch Clock Logic
There are two components to the punch clock application 
1. all interactions are hosted through api calls hosted on the backend of the website. 
2. users, or employees using the application, will interact at the terminal. (a mobile application) Using a `username`, employees will select themselves within the program, and intitate punches.

## Api Logic

`GET Request` used as the main punch logic. Each request populates a 'punch' variable. 2 or 4 punch variables are used, depending on if break tracking is selected. When reaching the limited number of punches, the total working hours are calculated, and sent to the corresponding timesheet database.

    - Tune punch clock logic upon app initialization.
    - Require break time punches (On/Off)
    - Scheduled Shifts (On/Off)
    - Shift Punch Buffer (delay in seconds)
    
After successful authentication, return associated token. 
Token patterns are of the below variety: 

    token TSA1xxxx
    token TSA2xxxx
    token TSA3xxxx
    
    The patterns are indicative of the associated tiers within the 
    account, and allow proper modularity with the API.

Within the API, the tokens are checked, leading to conditional logic within the API call. For certain tiers, more or less information may be stored or returned.

    After storing punches, and reaching the set limit (1 or 3)
    all hours data is sent to the associated timesheet database
    
Calculations related to each employee and their hours worked for the week, are recorded and displayed within the Timesheet page. Specific and in depth hours are available to be expanded on.
