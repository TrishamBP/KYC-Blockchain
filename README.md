# Decentralised KYC Etherum
Know your customer, or KYC, as it is referred to, originated as a standard to combat the laundering of illicit money flowing from terrorism, organized crime, and drug trafficking. The primary process behind KYC is that governments and enterprises need to track customers for illegal and money laundering activities. Moreover, KYC also enables banks to understand their customers and their financial dealings better. This helps them manage their risks and make better decisions.KYC may be a manual, time-consuming, and redundant across institutions. Sharing KYC information on Blockchain would enable financial institutions to deliver better compliance outcomes, increase efficiency, and improve customer experience.
## Problem
Each bank has its own KYC process set up. Due to this, customers have to do KYC separately for each individual bank.The lack of KYC standards makes it a time-consuming task to compile each KYC request.Due to disparate KYC specifications, customers have to provide the same information to different banking entities and industries. This becomes irksome for customers. Banks sometimes even follow up with customers to get more details for KYC. A recent study concluded that overheads for KYC in a bank increase the onboarding cost for a customer by 18% and the minimum time required to 26 days.
## Solution
The blockchain architecture and the DLT allow us to collect information from various service providers into one cryptographically secure and unchanging database that does not need a third party to verify the authenticity of the knowledge. It makes it possible to form a system where the user will only need to undergo the KYC procedure once to verify his/her identity.
## Smart Contract Flow
- The bank collects the information for the KYC from the customer.
- The information given by the customer includes username and customer data, which is the hash of the link for the customer data. This username is unique for each customer. 
- A bank creates the request for submission, which is stored in the smart contract.
- A bank then verifies the KYC data, which is then added to the customer list.
- Other banks can get customer information from the customer list.
- Other banks can also upvote/downvote customer data to demonstrate its authenticity. If the number of upvotes exceeds the number of downvotes, then the kycStatus of the corresponding customer is set to true. If a customer is downvoted by one-third of the banks on the network, then their kycStatus is changed to false, even if the number of upvotes is greater than the number of downvotes. For such logic, there should be a minimum of 5 or 10 banks on the network.
- In short, there are two conditions that are to be checked: the number of upvotes and downvotes, and whether the number of downvotes is greater than one-third of the total banks on the network.
- A bank can also report another bank if it finds that the other bank is corrupt and is verifying false customers. Such corrupt banks will then be banned from upvoting/downvoting further. If complaints against a particular bank are received from more than one-third of the total banks on the network, then that bank will be banned (i.e., isAllowedToVote will be set to false for that corrupt bank.)
### Admin Interface Methods

| **Function Name**        | **Input Params**                                     | **Return value**              | **Description**                                             |
| ------------------------ | ---------------------------------------------------- | ----------------------------- | ----------------------------------------------------------- |
| addBank()                | Bank Name, Eth address of bank, Bank reg number                                                 | -                             | To add new bank                                             |
| updateBankDetails()      | metamask `address` of bank,<br>email,<br>name        | -                             | To update the name & email of the bank                      |
| activateDeactivateBank() | metamask `address` of bank,<br>`isActivated` boolean | -                             | To activate & deactivate bank from the toggle               |

### Bank Interface Methods

| **Function Name**        | **Input Params**                                                             | **Return value**                                                 | **Description**                                                                                                     |
| ------------------------ | ---------------------------------------------------------------------------- | ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| getCustomersOfBank()     | pageNumber                                                                   | `totalPages` count,<br>KycRequest[]                              | To get all the list of customer kyc requests that were added by the current bank                                    |
| addKycRequest()          | Customer,<br>current `time` in epoch,<br>additional `notes`                  | -                                                                | To add new KYC request by adding new customer                                                                       |
| reRequestForKycRequest() | metamask `address` of the customer,<br>additional `notes`                    | -                                                                | If bank rejects the KYC verification or If customer rejects permission issue then this request can be rasided again |
| updateKycVerification()  | metamask `address` of customer,<br>`verified` boolean,<br>additional `notes` | -                                                                | To mark a customer as KYC verified                                                                                  |
| searchCustomers()        | metamask `address` of customer                                               | `bool` to say customer exists or not,<br>Customer,<br>KycRequest | To fetch customer by metamask address                                                                               |

### Customer Interface Methods
## Quick Start
Install the dependencies <br>
` npm install ` <br>
To compile your contracts in your Hardhat project, use the built-in compile task: <br>
` npx hardhat compile ` <br>
You can deploy in the localhost network following these steps: <br>
1. Start a local node <br>
` npx hardhat node `
2. Open a new terminal and deploy the smart contract in the localhost network. <br>
` npx hardhat run --network localhost scripts/deploy.js `
