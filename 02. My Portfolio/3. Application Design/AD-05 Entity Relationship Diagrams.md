
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
    users one -- many suggestions: has
    goals one -- many suggestions: has
    suggestions {
	    INTEGER id PK
	    INTEGER user_id FK
	    INTEGER goal_id FK
	    TEXT message
	    DATE created
	    BOOLEAN is_delivered
    }
    
    
```
