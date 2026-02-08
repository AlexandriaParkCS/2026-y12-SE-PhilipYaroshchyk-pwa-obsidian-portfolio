
``` mermaid
--- 
title: BreakingBank Entity Relationship Diagram
--- 
erDiagram
    users one -- many transactions : has
    users {
        INTEGER id PK
        TEXT name
        TEXT email
        TEXT password_hash
    }
    transactions {
        INTEGER id PK
        INTEGER user_id FK
        TEXT transaction_type
        FLOAT amout
        TEXT description
        DATE transaction_date
    }
    users one -- many goals : has
    goals one or zero -- one goals : linked
    goals {
	    INTEGER id PK
	    INTEGER user_id FK
	    TEXT goal_name
	    DATE start_time
	    DATE end_time
	    DATE created
	    DATE updated
	    parent_goal_id INTEGER FK
    }
    goals one -- many suggestions: has
    suggestions {
	    INTEGER id PK
	    INTEGER goal_id FK
	    TEXT message
	    DATE created
	    BOOLEAN is_delivered
    }
    
    
```
**Diagram guide:**
- Each user can have many transactions.
- Users can have many goals.
- Each goal can be linked to many other goals
- Each goal is linked to many suggestions

**Why user transactions and goals are not linked together?**
- Each transaction can be linked to multiple goals because the goal itself can be linked to other goals
- While its possible to have another table to link transactions to goals as a one to many relationships, it will not be used here. Instead we want to calculate goal tracking via connecting goals to transactions through the user. This way we can make goals modifiable, for example if the user decides to shorten the goal duration, then there is no need to update the transaction to goal link
