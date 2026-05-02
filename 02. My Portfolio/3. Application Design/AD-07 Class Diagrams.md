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
	Summary "1" *--> "0..n" Transaction
	Summary "1" *--> "0..n" Aggregation
	Transaction "0..n" <--* "1" User
	Goal "0..n" <--* "1" User

class User {
	int id
	str username
	str email
	str password_hash
	str password_salt
	
	+User(id, username, email, password_hash, password_salt)
}

class Transaction { 
	int id, 
	int user_id
	str transaction_type
	float amount
	date transaction_date
	str description
	
	+Transaction(id, user_id, transaction_type, amount, transaction-date, description)
} 

class Goal { 
	int id 
	int user_id 
	float amount 
	str goal_name
	date start_date
	date end_date
	date created_date
	date updated_date
	int parent_goal_id
	
	+Goal(id, user_id, amount, goal_name, start_date, created_date, updated_date, parent_goal_id)
	
}

class Aggregation {
	str name
	float amount
	
	+Aggregation(name, amount)
}

class Summary {
	float total
	str goal
	List[Transaction] transactions
	List[Aggregation] aggregations
	str tip
	
	+Summary(total, goal, transactions, aggregations, tip)
}

class UserService {
	SqlDb db
	Logger log
	
	+UserService(db, log)
	
	+signup(username, email, password) User
	+login(username, password) User
	+add_transaction(user_id, transaction_type, amount, date, description) Transaction
	+add_goal(user_id, amount, goal_name, start_date, end_date) Goal
	+get_user_goals(id) List[Goal]
	+get_user_transactions(id, limit, is_expense) List[Transaction]
	+get_transaction_summary_for_a_goal(user_id, goal_id) Summary
	
}

```