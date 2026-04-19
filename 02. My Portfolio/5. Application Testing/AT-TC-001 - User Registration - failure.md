
**Test Case ID:** TC-001

**Description:** 
Verify that a user cannot create an account with the password that fails validation

**Preconditions:**
- The Signup page is accessible.

**Steps:**
1. Navigate to the login/signup page.
2. Enter email address, name and password
3. Click the "Submit" button.
 
**Test Data:** 
- Email address: `example@example.com`
- User name: example
- Password: `Pass1234`

**Expected Result:** 
- User cannot register an account with a week password
- Clear error message is displayed


