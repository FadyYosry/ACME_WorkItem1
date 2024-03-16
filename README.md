# ACME System 1 (Verify Account Positions) employing the robust REFramework and Orchestrator queue

### Project Scenario
### REFramework Dispatcher
-  Initialization State:  Reading the config file, initiating "ACME System 1", and securely logging in.
-  Add Transaction Data: Scraping work items, filtering for WI1 with an open status, uploading the filtered data table onto the Orchestrator queue.
### REFramework Performer
-  Initialization State:  Config file read, applications "ACME System 1 and ACME System 3 Desktop" opened, and login executed for each.
-  Get Transaction Data:  Fetching transaction items from the queue.
- Process State:  Navigating within ACME System 1 to work item details using WIID, extracting relevant data (Client ID, Account Number, Account Amount), searching for account movements using Client ID in ACME System 3 Desktop, scraping the amount table, calculating the sum, and comparing it with the account amount.
- If Equal: Account Value Matches, marked as Completed, and updated.  If Not Equal: Account Value Not Matches, marked as Rejected, and updated.
