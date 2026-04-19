
**Test Case ID:** TC-012

**Description:** 
Verify that a user cannot load the goal their non-existent goal

**Preconditions:**
- User has logged in to the application
**Steps:**
1. manually set the url to contain the id of the invalid goal (either non-existent or the one that belongs to a different user)
 
**Test Data:** 
- case a) goal does not exist
- case b) goal exists but belongs to another user

**Expected Result:** 
- Goal summary is not loaded
- Clear error message is displayed



