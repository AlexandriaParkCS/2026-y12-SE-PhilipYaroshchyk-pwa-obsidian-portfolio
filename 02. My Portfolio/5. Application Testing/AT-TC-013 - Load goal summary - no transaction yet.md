
**Test Case ID:** TC-011

**Description:** 
Verify that a user can load goal summary when there is no transaction for the goal yet

**Preconditions:**
- User has logged in to the application
- User has created a goal that has no transaction for the goal date range yet
**Steps:**
1. Click on the `summary` for the goal on the dashboard page
 
**Test Data:** 
- There is a goal with the `2026-04-01 - 2026-04-30` date range
- there is no transaction for above date range

**Expected Result:** 
- Goal summary loads
- Goal summary contains the description
- Goal summary contains no charts
- Goal summary indicates that there is no transaction found for this goal

