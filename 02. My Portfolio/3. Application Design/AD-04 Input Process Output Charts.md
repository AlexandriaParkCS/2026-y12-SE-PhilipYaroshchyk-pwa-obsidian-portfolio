***Registration/Signup***
Registration process is a critical component of the application required for the user to access the application. 

*Input*
	- Username
	- Email address
	- Password (plain text)
*Process*
	- Sanitise and validate the full name, email address and password
	- Calculate a password hash
	- Attempt to create the new user entry in the database. 
	- If provided name or email already exists, reject the signup. Otherwise, create the user entry in the database and initialise a user session
*Output*
	- Success: 
		- User navigated to dashboard page
		- Authentication session token created
	- Failure: Error message


***Existing User Login***
*Input*
	- Username
	- Password (plain text)
*Process*
	- Sanitise and validate the name and password
	- Calculate a password hash
	- Check for an existing user using the username
	- If user not found, reject the login.
	- If user exists, compare the stored and calculated password hashes
	- If the the password hashes match, initialise a user session
	- Otherwise, reject the login
*Output*
	- Success: 
		- User navigated to dashboard page
		- Authentication session token created
	- Failure: Error message

***Create New Transaction***
*Input*
	- Transaction type
	- Amount
	- Transaction date
	- Description
*Process*
	- Sanitise and validate transaction type, amount, date and description
	- Get user id from user session 
	- Save transaction in the database
*Output*
	- User redirected to dashboard page

***Create New Goal***
*Input*
	- Name
	- Amount
	- Start date
	- End date
*Process*
	- Sanitise and validate goal name, amount, start and end date
	- Get user id from user session 
	- Save goal in the database
*Output*
	- User redirected to dashboard page


***Load Dashboard Page***

*Process*
	- Get user id from user session 
	- If no user id in session, navigate to login/signup page
	- If user id in session:
		- fetch goals for user
		- fetch recent expenses
		- fetch recent income entries
*Output*
	- Success:
		- User is presented with a dashboard page that contains:
			- Table that lists user goals (if user already created goals)
			- Table that lists recent income entries (if they exist)
			- Table that lists recent expense entries (if they exist)
	- Failure (user not logged in):
		- User is navigated to login/signup page	

***Load Summary Page***

*Input*
	- Summary id 
*Process*
	- User clicks on the link in the goals table of the dashboard (corresponds to goal id)
	- Application gets user id from user session 
	- If no user id in session, navigate to login/signup page
	- If user id in session:
		- fetch summary for a goal id requested
*Output*
	- Success:
		- User is presented with a summary page that contains:
			- Goal summary that includes name, target amount and current total amount to date 
			- "Transaction over time" line chart that contains users income and expenses over the goal lifetime 
			- Pie chart that shows total expenses grouped by expense type, for example Groceries/Utilities/Insurance, etc
			- "Analytics insight" section that shows the amount required to reach the goal target 
	- Failure (user not logged in):
		- User is navigated to login/signup page	