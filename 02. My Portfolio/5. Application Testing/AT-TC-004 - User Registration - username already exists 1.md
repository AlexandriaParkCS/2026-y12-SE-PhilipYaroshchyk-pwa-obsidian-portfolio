
**Test Case ID:** TC-004

**Description:** 
Verify that a user cannot create an account using the username that has already been used for registration


**Preconditions:**
- The Signup page is accessible.
- User with the`example` username has already been registered in the app

**Steps:**
1. Navigate to the login/signup page.
2. Enter email address, name and password
3. Click the "Submit" button.
 
**Test Data:** 
- Email address: `example@example.com`
- User name: ex
- Password: `P@ss12!$`

**Expected Result:** 
- User cannot register an account 
- Clear error message is displayed


