***Summary Generation***
The Goal's Summary Generation process is responsible for producing personalised financial summaries in the application. This process is initiated when a user requests to view the summary of their selected goal, typically by navigating to the Dashboard page and clicking on the summary link in the goals table.

![[structure1.drawio 1.png]]

At the top of the hierarchy is the Summary Generation module.
It is responsible for coordination of all submodules to retrieve, process, and present relevant financial data. It delegates tasks to three key data retrieval modules: Get Goal, Summarise Transactions , and Get Aggregations. These modules access the SQL database to collect the goal data, list of transactions for the goal as well as a list of expenses totals aggregated by type.

Once data is retrieved, the Summary Generation module uses it to create a summary object that is required for visualisation.  

The summary data is presented to the user in the UI via the "Income and Expenses Over Time" line and the "Expenses by Type" pie chart.

Algorithms: TODO
Flow chart: TODO

Algorithms:

`BEGIN GenerateDashboard`
	`UserSummary = GetUserData(UserID)`
	`TransactionSummary = GetTransactions(UserID)`
	`GoalSummary = GetGoals(UserID)`
	``
	`DISPLAY UserSummary`
	`IF TransactionSummary is empty`
		`DISPLAY Let's start budgeting!`
	`ELSE`
		`DISPLAY TransactionSummary`
	`ENDIF`
	`IF GoalSummary is empty`
		`DISPLAY Let's set some savings goals!`
	`ELSE`
		`DISPLAY GoalSummary`
	`ENDIF`
`END`

`BEGIN GetTransactions`
	`TransactionQuery = SELECT Transactions for UserID`
	`Transactions = RetrieveTransactions(TransactionQuery)`
	``
	`CategorisedTransactions = CategoriseTransactions(Transactions)`
	``
	`SummaryRow = 0`
	`FOR Category in CategorisedTransactions`
		`TRansactionSummary[SummaryRow] = Category`
		`NEXT CategoryRow`
			`FOR Transaction in Category`
				`TransactionSummary[SummaryRow] = Transaction`
				`NEXT CategoryRow`
			`ENDFOR`
	`ENDFOR`
	``
	`RETURN TransactionSummary`
`END`



![[Categorise Transactions Flow Chart.png]]

