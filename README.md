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
## Quick Start
Install the dependencies <br>
` npm install `
