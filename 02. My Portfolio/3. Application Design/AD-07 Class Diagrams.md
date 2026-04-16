This section contains the class diagram for the BreakingBank application. 

Goal, Transaction and User classes correspond to DB tables. UserService class has functionality to do:
- user login/signup 
- all interaction between the user and the database
- combining of data for presentation
Aggregation class is used for computed total of expenses for a given goal. Summary class contains a list of aggregations, list of transactions, name, total and a tip (analytics) for a goal. 

```mermaid
---
title: BreakingBank Class Diagram
---
classDiagram
	Summary --> Transaction
	Summary --> Aggregation
	Transaction --> User
	Goal --> User
	UserService --> User
	UserService --> Goal
	UserService --> Transaction
	UserService --> Summary
	UserService --> Aggregation

	

class User {
	-int _id
	-str _username
	-str _email
	-str _password_hash
	
	+get_id() int
	+get_username() str
	+get_email() str
	+get_password_hash() str
	
	+set_user_id()
	+set_username()
	+set_email()
	+set_password_hash()
}

class Transaction { 
	-int _id, 
	-int _user_id
	-str _transaction_type
	-float _amount
	-date _transaction_date
	-str _description
	
	+get_id() int 
	+get_user_id() int 
	+get_transaction_type() str 
	+get_amount() float 
	+get_transaction_date() float 
	+get_description() str
	
	+set_id(id)
	+set_user_id(id)
	+set_transaction_type(transaction_type)
	+set_amount(amount)
	+set_transaction_date(date)
	+set_description(description)
	
} 

class Goal { 
	-int _id, 
	-int _user_id, 
	-float _amount, 
	-str _goal_name,
	-date _start_date, 
	-date _end_date,
	-date _created_date, 
	-date _updated_date,
	-int _parent_goal_id,
	
	+get_id() int
	+get_user_id() int
	+get_amount() float
	+get_goal_name() str
	+get_start_date() date 
	+get_end_date() date 
	+get_created_date() date 
	+get_updated_date() date 
	+get_paren_goal_id() date 
	
	+set_id()
	+set_user_id()
	+set_amount()
	+set_goal_name()
	+set_start_date()
	+set_end_date()
	+set_created_date()
	+set_updated_date()
	+set_paren_goal_id()
}

class Aggregation {
	-str _name
	-float _amount
	
	+get_name() str
	+get_amount() float
	+set_name(name)
	+set_amount(amount)
}

class Summary {
	-float total
	-str goal
	-List[Transaction] transactions
	-List[Aggregation] aggregations
	-str tip
}

class UserService {
	--SqlDb db
	
	+signup(username, email, password) User
	+login(username, password) User
	+add_transaction(user_id, transaction_type, amount, date, description) Transaction
	+add_goal(user_id, amount, goal_name, start_date, end_date) Goal
	+get_user_goals(id) List[Goal]
	+get_user_transactions(id, limit, is_expense) List[Transaction]
	+get_transaction_summary_for_a_goal(user_id, goal_id) Summary
	
}

```