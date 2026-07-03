# QA Test Plan: E-Commerce Web Application (Automation Exercise)

## 1. Document Control
*   **Project Name:** Automation Exercise Manual Testing Practice
*   **Version:** 1.0
*   **Date:** July 3, 2026
*   **Author:** Lead QA Engineer
*   **Target SUT (System Under Test):** [Automation Exercise](https://automationexercise.com)

---

## 2. Introduction & Objectives
The purpose of this Test Plan is to define the testing strategy, scope, environment, and deliverables for the manual testing of the **Automation Exercise** website. 

The primary objective is to verify that the core e-commerce functionalities (user registration, login/logout, product catalog, search, shopping cart, and checkout flow) operate in accordance with standard functional requirements and user expectations, ensuring a bug-free and seamless user experience.

---

## 3. Scope of Testing

### 3.1 In-Scope
Testing will cover the following key functional modules:
1.  **User Registration & Account Management:** Creating accounts, checking duplicate signups, updating profiles, and deleting accounts.
2.  **Authentication (Login/Logout):** Successful login with valid credentials, error handling with invalid credentials, and session termination.
3.  **Product Catalog & Search:** Navigation, category filtering, search keyword accuracy, and viewing product details.
4.  **Shopping Cart:** Adding/removing items, modifying quantities, and persistence of cart items.
5.  **Checkout & Payments:** Address verification, checkout flows, dummy credit card processing, and order confirmation.
6.  **Contact Us & Subscription:** Contact form submissions (with file upload validation) and newsletter subscription.
7.  **API Testing:** Verification of 12+ API routes covering products, brands, search, and user accounts.

### 3.2 Out-of-Scope
The following types of testing are excluded from this project phase:
*   **Performance & Load Testing:** Testing the system's behavior under high concurrent user load.
*   **Security Vulnerability Assessment:** Comprehensive penetration testing, database injection scans, etc.
*   **Actual Payment Transactions:** Verification of real payment integrations (only mock payment details will be used).

---

## 4. Test Strategy & Methodologies

### 4.1 Functional Testing
Black-box testing techniques (equivalence partitioning, boundary value analysis) will be applied to verify inputs, forms, and business logic.

### 4.2 UI & Usability Testing
Verification of page layouts, responsive design on different viewports, navigation flow, and visual consistency against modern UI guidelines.

### 4.3 Cross-Browser & Compatibility Testing
Tests will be executed manually across different browsers to identify compatibility issues:
*   Google Chrome (v120+)
*   Mozilla Firefox (v120+)
*   Microsoft Edge (v120+)
*   Mobile viewports (simulated via Chrome DevTools responsive mode for iPhone and Android devices).

### 4.4 Regression Testing
Executed after defect fixes or UI updates to ensure that existing functionalities are not broken.

### 4.5 API Testing
Using **Postman** to execute API requests directly to the Automation Exercise API endpoints, validating status codes, response structures, and API logic.

---

## 5. Test Environment
*   **Production SUT URL:** `https://automationexercise.com`
*   **API Base URL:** `https://automationexercise.com/api/`
*   **Hardware:** Desktop PC (Windows 11) & Simulated Mobile Devices.
*   **Tools:**
    *   **Postman** (API testing & assertions)
    *   **Google Sheets / Excel** (Test Case management)
    *   **Jira / Trello** (Defect logging & tracking)
    *   **Chrome DevTools** (Inspection of DOM elements, console logs, and network traffic)

---

## 6. Entry & Exit Criteria

### 6.1 Entry Criteria
*   The test environment (`https://automationexercise.com`) is live and accessible.
*   Test Plan and Test Cases are documented and reviewed.
*   Postman API collections are structured.

### 6.2 Exit Criteria
*   100% of defined test cases have been executed.
*   Overall test case pass rate is $\ge 95\%$.
*   All identified defects are logged in the defect tracker.
*   No **Critical** or **High** severity defects remain open without business sign-off or mitigation plans.
*   All API tests are executed with successful assertions.

---

## 7. Defect Severity & Priority Matrix

| Severity | Description |
| :--- | :--- |
| **Critical** | System crash, data loss, security vulnerability, or blocker of a core flow (e.g., unable to register, checkout crashes). |
| **High** | Major feature is broken or fails consistently (e.g., unable to add to cart, search returns error page). No workaround exists. |
| **Medium** | Minor feature failure, or a major feature with a reasonable workaround (e.g., sorting displays incorrectly, cart badge count delays). |
| **Low** | Cosmetic issues, typos, font mismatches, or layout alignment issues that do not impact functionality. |

| Priority | Action Timeline |
| :--- | :--- |
| **High (P1)** | Fix immediately; blocks testing progress or critical release flows. |
| **Medium (P2)** | Fix in the next build or before release. |
| **Low (P3)** | Fix if time permits; cosmetic or non-blocking issues. |

---

## 8. Test Deliverables
At the end of the test cycle, the following artifacts will be delivered:
1.  **Test Plan** (This document)
2.  **Test Case Suite** (50+ cases in `.md` and `.csv` formats)
3.  **Defect Log** (15+ bugs in `.md` and `.csv` formats)
4.  **Postman Collection & Environment files** (`.json` files for API testing)
5.  **Test Summary Dashboard** (Visualized in `README.md`)
