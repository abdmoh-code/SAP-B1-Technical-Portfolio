# Service-Type Delivery Restriction

## Business Problem

The organization required Delivery documents to be created only for inventory-managed items.

Users were able to create Delivery documents using service-type transactions, which did not align with the company's operational processes and created inconsistencies in document handling.

## Investigation

The document creation process was reviewed to understand how SAP Business One differentiates between item-based and service-based transactions.

The objective was to identify a validation point capable of preventing the creation of service-type Delivery documents while allowing valid inventory deliveries to proceed normally.

## Technical Analysis

SAP Business One stores document type information that identifies whether a transaction is item-based or service-based.

A Transaction Notification was selected because it allows validation before the document is committed to the database.

The solution required:

* Detecting Delivery document creation events
* Identifying the document type
* Blocking service-type transactions
* Returning a meaningful error message to users

## Solution

Implemented a SAP HANA Transaction Notification that validates the document type during Delivery creation.

When a service-type Delivery is detected, the transaction is blocked and the user receives a validation message explaining the restriction.

Item-based Delivery documents continue through the standard process without interruption.

## Outcome

The organization achieved greater process consistency by ensuring that Delivery documents were used only for inventory-related transactions.

The solution reduced the risk of process deviations and aligned system behavior with operational requirements.

## Skills Demonstrated

* SAP Business One
* SAP HANA SQL
* Transaction Notifications
* Business Rule Enforcement
* ERP Customization
* Process Control
* Troubleshooting
