Loan Fee Amortization 

According to FASB loan origination fees and costs should be deferred and amortized over the life of the loan using level yield or effective interest method. This python code script would calculate and display an amortization Loan Net Fee schedule for a loan, taking into account Net Fees (origination fees - direct loan costs) 
Key Components
Initial Setup:
The loan principal, origination fee, direct loan costs, payments, stated interest rate, and loan term are defined.
An initial carrying amount is calculated by adjusting the loan principal with origination fees and direct costs.
Cash Flows and Effective Interest Rate:
Cash flows are initialized, and the effective interest rate is calculated using the internal rate of return (IRR) on these cash flows.
Amortization Schedule Calculation:
A loop iterates through each year of the loan term.
For each year, it calculates the stated interest, expected remaining principal, and updates the remaining principal using actual values if provided.
Prepayment amounts are calculated if the actual principal differs from the expected principal.
Amortization, interest income, and other financial metrics are calculated and stored.
Handling Edge Cases
Case 1: No actual payment history (e.g., new loan where the first payment starts in the future).
Action: No payments or adjustments are necessary at this stage.
Input: Loan principal: $100,000, Origination fee: $3,000, Direct loan costs: $1,000, Payments: $16,275, Stated interest rate: 10%, Loan term: 10 years, Actual principal balances: []
# Output : 
Effective Interest Rate: 0.10472982887457327

Case 2: With payment history, the expected remaining balance matches the actual balance history for the month.
Action: Proceed as expected without adjustments.
# Input : loan_principal = 100000, origination_fee = 3000, direct_loan_costs = 1000, Payments = 16275, stated_interest_rate = 0.10, loan_term = 10,actual_principal_balances = [[93725, 1],[86822, 2],[79229, 3]]
#Output: Effective Interest Rate: 0.10472982887457327

Case 3: With payment history, the expected remaining balance does not match the actual balance history for the month.
Action: The difference between the expected remaining balance and the actual balance is treated as the prepayment amount towards the principal. The payment period reduces the loan term, and the net fee is amortized according to prepayment events.
# Input : loan_principal = 100000, origination_fee = 3000, direct_loan_costs = 1000, Payments = 16275, stated_interest_rate = 0.10, loan_term = 10,actual_principal_balances = [[93725, 1],[86822, 2],[69229, 3]]
#Output: Effective Interest Rate: 0.10472982887457327
Note: The Year 3 balance decreased from 79,229 to 69,229, with the $10,000 difference shown as the prepayment amount.

Case 4: With payment history, the expected remaining balance does not match the actual balance history for a period but matches a prior period's remaining or actual balance.
Action: This scenario indicates that the customer did not make a payment for the period. The payment period increases the loan term, and the net fee should not be amortized for the missing period. Missing payments (Year 2 and 3 ) is filtered for display 
# Input : loan_principal = 100000, origination_fee = 3000, direct_loan_costs = 1000, Payments = 16275, stated_interest_rate = 0.10, loan_term = 10,actual_principal_balances = [[93725, 1],[93725, 2],[93725, 3]]
#Output: Effective Interest Rate: 0.10472982887457327
Note: The balances for Years 2 and 3 remain unchanged and match the Year 1 balance, indicating that no payments were made in Years 2 and 3 and loan periods extended to Year 11 and 12 

