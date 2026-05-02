
**Test Case ID:** TC-006

**Description:** 
Verify that a user cannot login when they provide incorrect credentials

**Preconditions:**
- The Login page is accessible.
- User with the`example` username has already been registered in the app

**Steps:**
1. Navigate to the login/signup page.
2. Enter the test data in the login form: 
	1. name: `example`
	2. password: `P@ss22!$`
3. Click the "Login" button.
 
**Test Data:** 
- User name: `example`
- Password: `P@ss22!$`

**Expected Result:** 
- User cannot login to the app
- Clear error message is shown

