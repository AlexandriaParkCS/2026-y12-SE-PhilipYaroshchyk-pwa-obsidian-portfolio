
**Test Case ID:** TC-001

**Description:** 
Verify that a user cannot create an account with the password that fails validation

**Preconditions:**
- The Signup page is accessible.

**Steps:**
1. Navigate to the login/signup page.
2. Enter the test data in the signup form:
	1. email address: `example@example.com` 
	2. name: `example`
	3. password: `Pass1234` 
3. Click the "Submit" button.

**Test Data:** 
- Email address: `example@example.com`
- User name:`example`
- Password: `Pass1234`

**Expected Result:** 
- User cannot register an account with a week password
- Clear error message is displayed


