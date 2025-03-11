# Manual Testing on Registration Page

This repository contains manual testing documents for a registration form, showing step-by-step testing and how issues are tracked. It includes clear test cases, bug reports, and summary reports. Both positive and negative scenarios are covered, with results marked as Passed, Failed, or Warning to reflect real-life testing.

## **Features Tested**  
- Validate username length  
- Enforce password rules (special characters, uppercase letters, and minimum length)  
- Ensure correct format for email and phone number  
- Validate Date of Birth (DOB) to prevent future dates  
- Verify selection of gender and country fields  
- Require acceptance of terms and conditions via checkbox  
- Conduct XSS and security testing on input fields  
- Prevent duplicate email registrations

## **Sample Test Case Document** 
---

| **Test Case ID** | **Test Description** | **Preconditions** | **Test Data** | **Test Steps** | **Expected Result** | **Actual Result** | **Status** | **Comments/Notes/Remarks** |
|------------------|----------------------|-------------------|---------------|----------------|---------------------|-------------------|------------|----------------------------|
| TC_01 | Verify all fields accept valid data | NA | Username: `user123`<br>Password: `Test@1234`<br>Email: `test@example.com`<br>Phone: `1234567890`<br>DOB: `1990-10-10`<br>Gender: Male<br>Country: USA | 1. Open registration page<br>2. Fill all fields<br>3. Submit | Registration successful | As expected | Pass | All fields handled valid data correctly |
| TC_02 | Verify username less than 5 characters | NA | Username: `usr`<br>Password: `Test@1234` | Enter username and submit | Error: "Username must be at least 5 characters" | Error message not displayed | Failed | Error handling issue |
| TC_03 | Verify username exceeding 15 characters | NA | Username: `verylongusername12345`<br>Password: `Test@1234` | Enter username and submit |

---
# **Sample Bug Report**

| **Bug ID** | **Bug Title** | **Test Case ID** | **Severity** | **Priority** | **Status** | **Description** | **Steps to Reproduce** | **Expected Result** | **Actual Result** | **Assigned To** | **Comments** |
|------------|---------------|------------------|--------------|--------------|------------|----------------|------------------------|--------------------|------------------|----------------|-------------|
| **BUG_001** | Error message not displayed for short username | TC_02 | Medium | High | Open | The error message for usernames shorter than 5 characters is not showing. | 1. Open registration page<br>2. Enter `usr` as username<br>3. Click Submit | Error: "Username must be at least 5 characters" | No error message displayed | Dev Team | Validation issue |
| **BUG_002** | Username accepted despite exceeding character limit | TC_03 | High | High | Open | Username with more than 15 characters is accepted even though an error message is shown. | 1. Open registration page<br>2. Enter `verylongusername12345` as username<br>3. Click Submit | Error: "Username must not exceed 15 characters" and form blocked | Form accepted input | Dev Team | Backend validation missing |
---

# **Test Execution Summary Report**

| **Total Test Cases** | **Passed** | **Failed** | **Warning** | **Blocked** |
|----------------------|------------|------------|-------------|-------------|
| 20                   | 13         | 4          | 3           | 0           |

## Defects Summary

| **Total Defects Found** | **Critical** | **High** | **Medium** | **Low** |
|-------------------------|--------------|----------|------------|---------|
| 6                       | 2            | 2        | 1          | 1       |

---
# **Recommendation**
- Apply robust validation for password requirements, ensuring compliance with minimum length and digit inclusion rules.  
- Correct backend logic to reject usernames exceeding 15 characters.  
- Ensure the Terms and Conditions checkbox remains editable after form submission.  
- Enhance the Country Dropdown functionality to preserve the selected value upon resubmission.

---
