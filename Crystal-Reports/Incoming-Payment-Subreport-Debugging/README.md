# Incoming Payment Subreport Debugging

## Business Problem

An SAP Business One Incoming Payment Crystal Report contained a cash payment subreport that failed to display expected account and payment information.

The report was connected to SAP HANA and utilized data from Incoming Payments (ORCT) and the Chart of Accounts (OACT).

## Investigation

The issue was isolated to the Cash subreport.

A comparison was performed between a working and non-working version of the subreport query.

The only difference identified between the two datasets was the inclusion of the Project Code field (`PrjCode`).

### Non-Working Dataset

Included:

* Account Name
* Cash Account
* Cash Sum
* Cash Sum (Foreign Currency)
* Document Entry
* Project Code

### Working Dataset

Included:

* Account Name
* Cash Account
* Cash Sum
* Cash Sum (Foreign Currency)
* Document Entry

## Technical Analysis

The following tables were involved:

* ORCT (Incoming Payments)
* OACT (Chart of Accounts)

Further investigation against the SAP HANA database confirmed:

* The `PrjCode` field existed within ORCT.
* Project Code values were empty for the affected records.
* The organization was not actively using Project Codes within the Incoming Payment process.

Testing confirmed that removing the Project Code field from the subreport dataset restored normal report functionality.

## Solution

Removed the unused `PrjCode` field from the Cash subreport dataset.

The modified report was tested within a dedicated SAP Business One testing environment and subsequently deployed to the target company database.

## Outcome

The Cash subreport displayed correctly and all expected payment information became available to users.

The issue was resolved without affecting any business processes because Project Codes were not utilized within the client's Incoming Payment workflow.

## Skills Demonstrated

* SAP Business One
* SAP HANA
* Crystal Reports
* SQL Investigation
* Root Cause Analysis
* Report Troubleshooting
* ERP Support
