***Summary Generation***
The Goal's Summary Generation process is responsible for producing personalised financial summaries in the application. This process is initiated when a user requests to view the summary of their selected goal, typically by navigating to the Dashboard page and clicking on the summary link in the goals table.

![[structure1.drawio 1.png]]

At the top of the hierarchy is the Summary Generation module.
It is responsible for coordination of all submodules to retrieve, process, and present relevant financial data. It delegates tasks to three key data retrieval modules: Get Goal, Summarise Transactions , and Get Aggregations. These modules access the SQL database to collect the goal data, list of transactions for the goal as well as a list of expenses totals aggregated by type.

Once data is retrieved, the Summary Generation module uses it to create a summary object that is required for visualisation.  

The summary data is presented to the user in the UI via the "Income and Expenses Over Time" line and the "Expenses by Type" pie chart.

***Algorithms:***

- `get_transaction_summary` is a function used to combine the data that the UI requires to render the goal summary page:

`BEGIN get_transaction_summary_for_a_goal(user_id, goal_id)
	
	transactions = get_user_transactions_for_goal(user_id, goal_id)
	goal = get_goal_by_id(user_id, goal_id)
	aggregations = get_aggretated_user_expenses_for_goal(user_id, goal_id)
	
	total_amount = 0
	FOR tr IN transactions
		total_amount = total_amount + tr.amount
	ENDFOR	

	tip = compute_tip(total_amount, goal.amount)`
	
	summary = Summary(total_amount, goal, transactions, agggregations, tip)
	RETURN summary
`END`

- `get_user_transactions_for_goal` is a function used to fetch user transactions for a corresponding goal

`BEGIN get_user_transactions_for_goal(user_id, goal_id)`
	`matched_rows = SQL(WHERE user_id, goal_id)
	`transaction_list = []`
	`FOR row IN matched_rows`
		`transaction = map(row)`
		`APPEND(transaction_list, transaction)`
	`ENDIF`	
	`RETURN transaction_list`	
`END`

***Flow chart for the process that shows summary for a goal*** 

The flow chart below shows the process of rendering the summary page for a user for a given goal. 

![[show_summary.drawio.png]]