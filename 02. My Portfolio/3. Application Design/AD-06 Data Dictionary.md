Data dictionary that corresponds to the BreakingBad's Entity Relationship Diagram is shown below.

***User***

| Attribute     | Data Type | Bytes | Description                               | Example              |
| ------------- | --------- | ----- | ----------------------------------------- | -------------------- |
| username      | String    | 256   | Unique user name provided at registration | johnd, John Doe      |
| email         | String    | 64    | A valid and unique email address          | user@address.com     |
| password_hash | String    | 128   | bcript hash of a password                 | 5d41402abc4b2a761223 |
| password_salt | String    | 128   | bcript salt of a password                 | 243262243132242e786c |

***Transaction***

| Attribute        | Data Type | Bytes | Description                                                                                                                                                                                                                                                                                                                                                  | Example       |
| ---------------- | --------- | ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------- |
| amount           | Float     | 4     | Transaction amount. Negative values represent expenses and positive indicate income.                                                                                                                                                                                                                                                                         | 10.50         |
| date             | Date      | 4     | The date of the transaction.                                                                                                                                                                                                                                                                                                                                 | 2025-12-30    |
| description      | String    | 256   | Free text to describe the transaction (optional)                                                                                                                                                                                                                                                                                                             | Wollies/Coles |
| transaction_type | String    | 256   | One of the pre-selected values: - Income - all types<br>- Groceries<br>- Eating out<br>- Memberships<br>- Transportation<br>- Utilities<br>- Rent<br>- Mortgage payments<br>- Insurance<br>- Personal expenses<br>- Shopping spree / consumerism<br>- Investments<br>- Travelling / Holidays<br>- Gas<br>- Debt payments<br>- Hobbies<br>- other necessities | Groceries     |


***Goal***

| Attribute    | Data Type | Bytes | Description                                                   | Exaemple            |
| ------------ | --------- | ----- | ------------------------------------------------------------- | ------------------- |
| amount       | Float     | 4     | Monetary amount that this goal is meant to achieve in savings | 700.00              |
| goal_name    | String    | 256   | Free text to describe the goal.                               | Saving for a laptop |
| start_date   | Date      | 4     | Start date for the goal                                       | 2025-01-01          |
| end_date     | Date      | 4     | End date for the goal                                         | 2027-01-01          |
| created_date | Date      | 4     | Date the goal has been created                                | 2024-12-05          |
| updated_date | Date      | 4     | Date the goal has been updated (null if no updates)           | 2024-12-20/NULL     |

