# Get started with Decode AS2 Message

Connect to Applicability Statement 2 (AS2) - Decode AS2 Message to establish security and reliability when transmitting B2B messages over HTTP/S. It provides digital signing and encryption as well as acknowledgements via Message Disposition Notifications (MDN), which also leads to support for Non-Repudiation (NRR).

## Create the connection

### Prerequisites

* An Azure account; you can create a [free account](https://azure.microsoft.com/free)
* An integration account is required to use Decode EDIFACT message connector. See details on how to create an [integration account](https://azure.microsoft.com/en-us/documentation/articles/app-service-logic-enterprise-integration-accounts/), add [partners](https://azure.microsoft.com/en-us/documentation/articles/app-service-logic-enterprise-integration-partners/) and [AS2 agreement](https://azure.microsoft.com/en-us/documentation/articles/app-service-logic-enterprise-integration-as2/) to it.

### Connect to Decode AS2 Message using the following steps:

1. Create a Logic App.  [Create a logic app](https://azure.microsoft.com/en-us/documentation/articles/app-service-logic-create-a-logic-app/) provides an example.

2. This connector does not have any triggers. Use other triggers to start the logic app, such as a Request trigger.  In the Logic App designer, add a trigger and add an action.  Select Show Microsoft managed APIs in the drop down list and then enter “AS2” in the search box.  Select AS2 – Decode AS2 Message

3. If you haven’t previously created any connections to Integration account, you are prompted for the connection details

4. Enter the integration account details.  Properties with an asterisk are required

	| Property   | Details |
	| --------   | ------- |
	| Connection Name *    | Enter any name for your connection |
	| Integration Account * | Enter the integration account name; Be sure your integration account and Logic app are in the same Azure location |

Once complete, your coonection details look similar to the following

5. Select Create

6. Notice the connection has been created.  Now, proceed with the other steps in your Logic App

7. Select Body and Headers from Request outputs

## The AS2 Decode does the following

* Processes AS2/HTTP headers
* Verifies the signature, if the message was signed
* Decrypts the messages, if the message was encrypted (for an EDI/AS2 message, not an MDN)
* Decompresses the message, if the message was compressed
* Reconciles a received MDN with the original outbound message
* Updates and correlates records in the non-repudiation database
* Writes records for AS2 status reporting
* Determines whether an MDN is required, and whether the MDN should be synchronous or asynchronous based on configuration in AS2 agreement
* Generates an AS2 MDN
* If the MDN is synchronous, sets the sendMDNAsynchronously value False; if asynchronous, sets it True.
* Sets the correlation tokens and properties on the MDN