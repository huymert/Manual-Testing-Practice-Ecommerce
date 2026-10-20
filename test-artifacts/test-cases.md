# Master Test Cases Specification: Automation Exercise

> **Testing Role:** Senior QA Engineer / QA Lead  
> **Total Designed Cases:** 54 | **Execution Rate:** 100% | **Pass Rate:** 70.37% (38 Passed, 16 Failed)

This suite covers end-to-end user journeys and technical testing techniques including **Equivalence Partitioning (EP)**, **Boundary Value Analysis (BVA)**, **Security Input Sanitization**, **Session Lifecycle**, and **Cross-Browser Compatibility**.

---

## 📊 Master Test Cases Matrix

| TC ID | Title | Module | Priority | Type | Status | Linked Defect |
| :--- | :--- | :--- | :--- | :--- | :---: | :---: |
| TC-REG-001 | Register successfully with all valid required fields | Registration & Account Management | High (P1) | Functional - Positive (Happy Path) | ✅ **Pass** | - |
| TC-REG-002 | Register successfully with all optional fields filled | Registration & Account Management | Medium (P2) | Functional - Positive (Optional Fields) | ✅ **Pass** | - |
| TC-REG-003 | Register with an email address that is already registered | Registration & Account Management | High (P1) | Functional - Negative (Equivalence Partitioning) | ✅ **Pass** | - |
| TC-REG-004 | Register with invalid email format | Registration & Account Management | High (P1) | Boundary & Format Validation (EP) | ✅ **Pass** | - |
| TC-REG-005 | Register leaving required fields empty | Registration & Account Management | High (P1) | Functional - Negative (Mandatory Validation) | ❌ **Fail** | [BUG-001](bug-reports.md#bug-001) |
| TC-REG-006 | Register with special characters / SQL syntax in Name fields | Registration & Account Management | High (P1) | Security - Input Sanitization & SQLi | ❌ **Fail** | [BUG-002](bug-reports.md#bug-002) |
| TC-REG-007 | Register with password less than minimum length | Registration & Account Management | Medium (P2) | Boundary Value Analysis (BVA) | ✅ **Pass** | - |
| TC-REG-008 | Verify password fields hide inputs by default | Registration & Account Management | Medium (P2) | UI / Security (Masking) | ✅ **Pass** | - |
| TC-REG-009 | Verify account creation immediately establishes session | Registration & Account Management | High (P1) | Session Management & State Transition | ✅ **Pass** | - |
| TC-REG-010 | Verify delete account functionality removes user from system | Registration & Account Management | High (P1) | Functional & Data Lifecycle (CRUD - Delete) | ✅ **Pass** | - |
| TC-LOG-001 | Login successfully with valid registered credentials | Login & Logout | High (P1) | Functional - Positive (Authentication) | ✅ **Pass** | - |
| TC-LOG-002 | Login failed with unregistered email | Login & Logout | High (P1) | Functional - Negative (Authentication) | ✅ **Pass** | - |
| TC-LOG-003 | Login failed with incorrect password for registered email | Login & Logout | High (P1) | Functional - Negative (Authentication) | ✅ **Pass** | - |
| TC-LOG-004 | Login failed with empty email and password fields | Login & Logout | Medium (P2) | Boundary & Input Validation (EP) | ✅ **Pass** | - |
| TC-LOG-005 | Verify session persistence using 'Remember me' option | Login & Logout | Medium (P2) | Session Persistence & Cookie Handling | ❌ **Fail** | [BUG-003](bug-reports.md#bug-003) |
| TC-LOG-006 | Verify password field toggles input visibility | Login & Logout | Low (P3) | UI / Usability (Password Masking Toggle) | ✅ **Pass** | - |
| TC-LOG-007 | Verify successful logout terminates user session | Login & Logout | High (P1) | Session Management & Security (Logout) | ✅ **Pass** | - |
| TC-LOG-008 | Verify redirection to login page when accessing checkout without authorization | Login & Logout | High (P1) | Security - Access Control & Authorization | ✅ **Pass** | - |
| TC-LOG-009 | Verify account lockout after multiple failed login attempts | Login & Logout | Medium (P2) | Security - Rate Limiting & Account Lockout | ✅ **Pass** | - |
| TC-LOG-010 | Verify reset password request functionality | Login & Logout | Medium (P2) | Functional - Password Recovery Flow | ✅ **Pass** | - |
| TC-CAT-001 | Verify navigation to Product page and product list rendering | Product Catalog & Search | High (P1) | Functional - Catalog Rendering & Pagination | ✅ **Pass** | - |
| TC-CAT-002 | Search for a product using exact matching product name | Product Catalog & Search | High (P1) | Functional - Search (Exact Match) | ✅ **Pass** | - |
| TC-CAT-003 | Search for a product using partial match query | Product Catalog & Search | Medium (P2) | Functional - Search (Partial Match / EP) | ✅ **Pass** | - |
| TC-CAT-004 | Search for a product with non-existent keyword | Product Catalog & Search | Medium (P2) | Functional - Search (Negative / Zero Results) | ✅ **Pass** | - |
| TC-CAT-005 | Search for a product using special characters | Product Catalog & Search | High (P1) | Security & Error Handling (Special Chars / EP) | ❌ **Fail** | [BUG-004](bug-reports.md#bug-004) |
| TC-CAT-006 | Verify category filtering displays correct matching items | Product Catalog & Search | High (P1) | Functional - Taxonomy & Category Filtering | ✅ **Pass** | - |
| TC-CAT-007 | Verify category filtering works correctly on mobile viewports | Product Catalog & Search | High (P1) | Compatibility & Mobile Responsive UI | ❌ **Fail** | [BUG-005](bug-reports.md#bug-005) |
| TC-CAT-008 | Verify viewing details of a specific product | Product Catalog & Search | High (P1) | Functional - Product Details & SKU View | ✅ **Pass** | - |
| TC-CAT-009 | Verify brand sidebar filters products correctly | Product Catalog & Search | Medium (P2) | Functional - Brand Facet Filtering | ✅ **Pass** | - |
| TC-CAT-010 | Verify 'Back to Products' link on details page returns to previous list state | Product Catalog & Search | Low (P3) | UI / State Preservation & Navigation | ❌ **Fail** | [BUG-006](bug-reports.md#bug-006) |
| TC-CRT-001 | Add a single product to cart from Products list | Shopping Cart & Cart Actions | High (P1) | Functional - Positive (Cart Addition) | ✅ **Pass** | - |
| TC-CRT-002 | Add multiple products to cart and verify details | Shopping Cart & Cart Actions | High (P1) | Functional - Positive (Multi-item Cart) | ✅ **Pass** | - |
| TC-CRT-003 | Add same product multiple times and verify quantity increment | Shopping Cart & Cart Actions | High (P1) | Business Logic - Cart Accumulation | ✅ **Pass** | - |
| TC-CRT-004 | Verify add is blocked for zero-stock / out-of-stock items | Shopping Cart & Cart Actions | High (P1) | Business Logic & Inventory Control | ❌ **Fail** | [BUG-007](bug-reports.md#bug-007) |
| TC-CRT-005 | Modify quantity directly in product details before adding | Shopping Cart & Cart Actions | Medium (P2) | Boundary Value Analysis (BVA - Quantity) | ✅ **Pass** | - |
| TC-CRT-006 | Verify negative or zero quantities are blocked in cart input | Shopping Cart & Cart Actions | High (P1) | Boundary Value Analysis (BVA - Negative / Zero) | ❌ **Fail** | [BUG-008](bug-reports.md#bug-008) |
| TC-CRT-007 | Remove an item from cart using the 'X' button | Shopping Cart & Cart Actions | Medium (P2) | UI / Event Handling & Cart Removal | ❌ **Fail** | [BUG-009](bug-reports.md#bug-009) |
| TC-CRT-008 | Verify cart count badge in header updates dynamically | Shopping Cart & Cart Actions | Medium (P2) | UI / Reactive State (Badge Counter) | ❌ **Fail** | [BUG-010](bug-reports.md#bug-010) |
| TC-CRT-009 | Verify cart persistence across logout/login sessions | Shopping Cart & Cart Actions | High (P1) | Session Management & Cart Persistence | ✅ **Pass** | - |
| TC-CRT-010 | Verify subtotal and grand total update automatically on quantity change | Shopping Cart & Cart Actions | High (P1) | Business Logic & Calculation Engine | ✅ **Pass** | - |
| TC-CHK-001 | Verify checkout navigation for logged-in user | Checkout, Billing & Payments | High (P1) | Functional - Positive (Checkout Navigation) | ✅ **Pass** | - |
| TC-CHK-002 | Verify Address Details page displays correct default user details | Checkout, Billing & Payments | High (P1) | Data Integrity & Profile Auto-fill | ✅ **Pass** | - |
| TC-CHK-003 | Verify user can add comments/notes to order | Checkout, Billing & Payments | Low (P3) | Functional - Order Notes / Comments | ✅ **Pass** | - |
| TC-CHK-004 | Verify Payment page details input masking | Checkout, Billing & Payments | Medium (P2) | UI / Security (Payment Form Masking) | ✅ **Pass** | - |
| TC-CHK-005 | Verify place order with valid promo code discounts price | Checkout, Billing & Payments | High (P1) | Business Logic & Promo Code Engine | ❌ **Fail** | [BUG-011](bug-reports.md#bug-011) |
| TC-CHK-006 | Verify checkout button is active and functional in all major browsers | Checkout, Billing & Payments | High (P1) | Cross-Browser Compatibility | ❌ **Fail** | [BUG-012](bug-reports.md#bug-012) |
| TC-CHK-007 | Pay using credit card with 2-digit expiration year | Checkout, Billing & Payments | High (P1) | Boundary & Format Validation (BVA - Date) | ❌ **Fail** | [BUG-013](bug-reports.md#bug-013) |
| TC-CHK-008 | Pay using credit card with standard valid parameters | Checkout, Billing & Payments | High (P1) | Functional - Positive (End-to-End Payment) | ✅ **Pass** | - |
| TC-CHK-009 | Verify Tax/VAT calculations are correct on order breakdown | Checkout, Billing & Payments | High (P1) | Business Logic & Financial Calculations | ❌ **Fail** | [BUG-014](bug-reports.md#bug-014) |
| TC-CHK-010 | Verify order confirmation screen displays Invoice Download link | Checkout, Billing & Payments | Medium (P2) | Functional - Order Completion & Invoice Link | ✅ **Pass** | - |
| TC-CHK-011 | Verify Download Invoice option outputs valid document | Checkout, Billing & Payments | Medium (P2) | Functional - File Download & PDF Verification | ✅ **Pass** | - |
| TC-CHK-012 | Verify order confirmation email formatting | Checkout, Billing & Payments | Low (P3) | Integration & Email Template Rendering | ❌ **Fail** | [BUG-015](bug-reports.md#bug-015) |
| TC-GEN-001 | Submit Contact Us form with unsupported attachment formats | General & Contact Us | High (P1) | Security & File Upload Validation (EP) | ❌ **Fail** | [BUG-016](bug-reports.md#bug-016) |
| TC-GEN-002 | Verify newsletter subscription validation | General & Contact Us | Low (P3) | Functional - Subscription & Email Validation | ✅ **Pass** | - |

---

## 📝 Detailed Test Cases Specification

### 📂 Module: Registration & Account Management

#### 🛠️ TC-REG-001: Register successfully with all valid required fields
* **Module:** Registration & Account Management
* **Priority:** `High (P1)` | **Type / Technique:** `Functional - Positive (Happy Path)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the Signup page (https://automationexercise.com/login)
* **Test Data:** `Name: John Doe, Email: john.qa.valid2026@testmail.com, Pass: P@ssw0rd2026, First: John, Last: Doe, Address: 123 Automation Blvd, State: California, City: Los Angeles, Zip: 90001, Mobile: +15551234567`
* **Steps to Execute:**
  1. Enter valid Name and Email in the Signup section.
  2. Click 'Signup' button.
  3. Complete mandatory fields on 'Enter Account Information' form.
  4. Click 'Create Account' button.
* **Expected Result:** Account is created successfully; user session is active; 'ACCOUNT CREATED!' page is displayed with Continue button.
* **Actual Result:** Account created successfully with unique ID; redirected to '/account_created'; header displays 'Logged in as John Doe'.

---

#### 🛠️ TC-REG-002: Register successfully with all optional fields filled
* **Module:** Registration & Account Management
* **Priority:** `Medium (P2)` | **Type / Technique:** `Functional - Positive (Optional Fields)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the Signup page
* **Test Data:** `Title: Mr, DOB: 15/08/1992, Company: QA Enterprise, Address2: Suite 400, Newsletter: Checked, Special Offers: Checked`
* **Steps to Execute:**
  1. Enter Name and Email, click 'Signup'.
  2. Fill all mandatory fields.
  3. Fill optional fields: Title, Date of Birth, Newsletter checkbox, Special offers checkbox, Company, Address 2.
  4. Click 'Create Account'.
* **Expected Result:** Account is created successfully with all profile details saved correctly in database.
* **Actual Result:** All optional demographic and newsletter preferences persisted in profile record; welcome email queued.

---

#### 🛠️ TC-REG-003: Register with an email address that is already registered
* **Module:** Registration & Account Management
* **Priority:** `High (P1)` | **Type / Technique:** `Functional - Negative (Equivalence Partitioning)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** An account with email 'existing_user@example.com' already exists in the system database.
* **Test Data:** `Name: Existing User, Email: existing_user@example.com`
* **Steps to Execute:**
  1. Enter Name and 'existing_user@example.com' in the Signup section.
  2. Click 'Signup' button.
* **Expected Result:** Form submission is blocked; inline error message 'Email Address already exist!' is displayed.
* **Actual Result:** Form submission intercepted; inline red alert 'Email Address already exist!' displayed; account not duplicated.

---

#### 🛠️ TC-REG-004: Register with invalid email format
* **Module:** Registration & Account Management
* **Priority:** `High (P1)` | **Type / Technique:** `Boundary & Format Validation (EP)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the Signup page
* **Test Data:** `Invalid emails: 'user@', 'user@domain', 'user.domain.com', '@example.com'`
* **Steps to Execute:**
  1. Enter Name and invalid email formats into Signup input.
  2. Click 'Signup' button.
* **Expected Result:** HTML5 validation error blocks form submission, requiring an '@' and a valid top-level domain format.
* **Actual Result:** Browser HTML5 validation tooltip 'Please include an @ in the email address' blocks submit.

---

#### 🛠️ TC-REG-005: Register leaving required fields empty
* **Module:** Registration & Account Management
* **Priority:** `High (P1)` | **Type / Technique:** `Functional - Negative (Mandatory Validation)`
* **Execution Status:** 🟥 **FAIL** (Ref: BUG-001)
* **Preconditions:** User is on the Signup page
* **Test Data:** `Name: Empty Tester, Email: empty_test_005@test.com, Blank fields: Password, First Name, Last Name, Address`
* **Steps to Execute:**
  1. Enter Name and valid Email and click 'Signup'.
  2. On the Account details page, leave mandatory fields (Password, First Name, Last Name, Address) completely empty.
  3. Click 'Create Account' button.
* **Expected Result:** Form validation triggers indicating empty required fields; page remains on details form and does not submit to server.
* **Actual Result:** Form validation bypassed; account created with NULL/empty mandatory fields; causing severe errors in checkout profile.
* **Linked Defect:** [BUG-001](bug-reports.md#bug-001)

---

#### 🛠️ TC-REG-006: Register with special characters / SQL syntax in Name fields
* **Module:** Registration & Account Management
* **Priority:** `High (P1)` | **Type / Technique:** `Security - Input Sanitization & SQLi`
* **Execution Status:** 🟥 **FAIL** (Ref: BUG-002)
* **Preconditions:** User is on the Signup page
* **Test Data:** `First Name: John' OR '1'='1, Last Name: O'Connor; DROP TABLE users;--`
* **Steps to Execute:**
  1. Enter valid email and signup.
  2. In 'First Name' or 'Last Name' input: John' OR '1'='1.
  3. Complete remaining fields and click 'Create Account'.
* **Expected Result:** Input is properly sanitized before database execution; names are stored as literal strings or rejected with validation message; no raw SQL errors shown.
* **Actual Result:** Raw database SQL exception traceback exposed on UI; unhandled database syntax error reveals backend table structure.
* **Linked Defect:** [BUG-002](bug-reports.md#bug-002)

---

#### 🛠️ TC-REG-007: Register with password less than minimum length
* **Module:** Registration & Account Management
* **Priority:** `Medium (P2)` | **Type / Technique:** `Boundary Value Analysis (BVA)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the Signup page
* **Test Data:** `Password: 'a' (1 character; boundary threshold min = 6 characters)`
* **Steps to Execute:**
  1. Enter valid Name and Email and click 'Signup'.
  2. Input a password of 1 character.
  3. Click 'Create Account'.
* **Expected Result:** Validation error is displayed indicating password must be at least 6 characters.
* **Actual Result:** Password field error displayed; form requires minimum 6 characters to proceed.

---

#### 🛠️ TC-REG-008: Verify password fields hide inputs by default
* **Module:** Registration & Account Management
* **Priority:** `Medium (P2)` | **Type / Technique:** `UI / Security (Masking)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the details signup form
* **Test Data:** `Password: SecretPassword#123`
* **Steps to Execute:**
  1. Type text into the Password field.
  2. Observe rendered characters in the DOM input element.
* **Expected Result:** Characters typed are masked as dots or asterisks for privacy (input type='password').
* **Actual Result:** Input masked with bullet characters; inspect element reveals type='password'.

---

#### 🛠️ TC-REG-009: Verify account creation immediately establishes session
* **Module:** Registration & Account Management
* **Priority:** `High (P1)` | **Type / Technique:** `Session Management & State Transition`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is filling the account creation form
* **Test Data:** `Valid registration profile data`
* **Steps to Execute:**
  1. Fill all required fields.
  2. Click 'Create Account'.
  3. Click 'Continue' on the Account Created confirmation page.
* **Expected Result:** Logged-in session is active, and header displays 'Logged in as [Username]'.
* **Actual Result:** Authentication cookie set; user header shows active session with username displayed.

---

#### 🛠️ TC-REG-010: Verify delete account functionality removes user from system
* **Module:** Registration & Account Management
* **Priority:** `High (P1)` | **Type / Technique:** `Functional & Data Lifecycle (CRUD - Delete)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is logged in
* **Test Data:** `Authenticated user: to_delete_user@example.com`
* **Steps to Execute:**
  1. Click 'Delete Account' link in the header menu.
  2. Confirm account deletion.
  3. Try logging in again with the deleted credentials.
* **Expected Result:** Account is deleted. Header shows 'ACCOUNT DELETED!'. Re-login attempt fails with incorrect credentials error.
* **Actual Result:** Account record purged; redirected to '/delete_account'; re-login fails with incorrect credentials.

---

### 📂 Module: Login & Logout

#### 🛠️ TC-LOG-001: Login successfully with valid registered credentials
* **Module:** Login & Logout
* **Priority:** `High (P1)` | **Type / Technique:** `Functional - Positive (Authentication)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** A registered user exists (test_qa@example.com / Password123)
* **Test Data:** `Email: test_qa@example.com, Password: Password123`
* **Steps to Execute:**
  1. Navigate to Login page.
  2. Enter 'test_qa@example.com' in the Login email field.
  3. Enter 'Password123' in the password field.
  4. Click 'Login' button.
* **Expected Result:** User is redirected to the home page, and header displays 'Logged in as [Name]'.
* **Actual Result:** Login successful; session cookie generated; redirected to home page with user menu displayed.

---

#### 🛠️ TC-LOG-002: Login failed with unregistered email
* **Module:** Login & Logout
* **Priority:** `High (P1)` | **Type / Technique:** `Functional - Negative (Authentication)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** Email 'not_registered@example.com' does not exist in system database.
* **Test Data:** `Email: not_registered@example.com, Password: Password123`
* **Steps to Execute:**
  1. Navigate to Login page.
  2. Enter 'not_registered@example.com' and password 'Password123'.
  3. Click 'Login'.
* **Expected Result:** Login fails. Error message 'Your email or password is incorrect!' is displayed.
* **Actual Result:** Alert banner 'Your email or password is incorrect!' displayed; password field cleared.

---

#### 🛠️ TC-LOG-003: Login failed with incorrect password for registered email
* **Module:** Login & Logout
* **Priority:** `High (P1)` | **Type / Technique:** `Functional - Negative (Authentication)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** Registered email exists (test_qa@example.com)
* **Test Data:** `Email: test_qa@example.com, Password: WrongPassword#99`
* **Steps to Execute:**
  1. Navigate to Login page.
  2. Enter 'test_qa@example.com' and incorrect password 'WrongPassword#99'.
  3. Click 'Login'.
* **Expected Result:** Login fails. Error message 'Your email or password is incorrect!' is displayed.
* **Actual Result:** Alert banner 'Your email or password is incorrect!' displayed; no sensitive account info leaked.

---

#### 🛠️ TC-LOG-004: Login failed with empty email and password fields
* **Module:** Login & Logout
* **Priority:** `Medium (P2)` | **Type / Technique:** `Boundary & Input Validation (EP)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the Login page
* **Test Data:** `Email: [EMPTY], Password: [EMPTY]`
* **Steps to Execute:**
  1. Leave email and password fields empty.
  2. Click 'Login'.
* **Expected Result:** HTML5 validation message is displayed on empty fields, blocking form submission.
* **Actual Result:** HTML5 'Please fill out this field' validation tooltip blocks submission.

---

#### 🛠️ TC-LOG-005: Verify session persistence using 'Remember me' option
* **Module:** Login & Logout
* **Priority:** `Medium (P2)` | **Type / Technique:** `Session Persistence & Cookie Handling`
* **Execution Status:** 🟥 **FAIL** (Ref: BUG-003)
* **Preconditions:** User is on the Login page with valid credentials
* **Test Data:** `Email: test_qa@example.com, Password: Password123, Checkbox: [x] Remember Me`
* **Steps to Execute:**
  1. Enter valid email and password.
  2. Check the 'Remember me' checkbox and log in.
  3. Close the browser window completely.
  4. Open browser again and navigate to homepage.
* **Expected Result:** User remains logged in without being prompted to login again (persistent session cookie).
* **Actual Result:** User session is completely wiped upon browser restart; session cookie lacks Max-Age/Expires header.
* **Linked Defect:** [BUG-003](bug-reports.md#bug-003)

---

#### 🛠️ TC-LOG-006: Verify password field toggles input visibility
* **Module:** Login & Logout
* **Priority:** `Low (P3)` | **Type / Technique:** `UI / Usability (Password Masking Toggle)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the Login page
* **Test Data:** `Password: SamplePass#2026`
* **Steps to Execute:**
  1. Enter password 'SamplePass#2026' in the password field.
  2. Click on the eye/toggle icon to show password.
  3. Click it again to hide.
* **Expected Result:** First click reveals password characters as plain text; second click masks them again.
* **Actual Result:** Password visibility toggle unmasks text to plain characters and re-masks on click.

---

#### 🛠️ TC-LOG-007: Verify successful logout terminates user session
* **Module:** Login & Logout
* **Priority:** `High (P1)` | **Type / Technique:** `Session Management & Security (Logout)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is logged in and on the homepage
* **Test Data:** `Active authenticated session`
* **Steps to Execute:**
  1. Click 'Logout' link in the header menu.
  2. Click browser 'Back' button.
* **Expected Result:** User is redirected to the login page. Clicking Back does not restore the logged-in session, and private pages are inaccessible.
* **Actual Result:** Session token invalidated; redirected to login; back button displays cached login prompt.

---

#### 🛠️ TC-LOG-008: Verify redirection to login page when accessing checkout without authorization
* **Module:** Login & Logout
* **Priority:** `High (P1)` | **Type / Technique:** `Security - Access Control & Authorization`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is anonymous / not logged in
* **Test Data:** `Target URL: https://automationexercise.com/checkout`
* **Steps to Execute:**
  1. Directly paste '/checkout' URL in browser address bar.
  2. Hit Enter.
* **Expected Result:** Access is denied; system redirects user to Login page with a prompt to authenticate.
* **Actual Result:** Unauthenticated checkout attempt redirected to '/login' with returnUrl parameter preserved.

---

#### 🛠️ TC-LOG-009: Verify account lockout after multiple failed login attempts
* **Module:** Login & Logout
* **Priority:** `Medium (P2)` | **Type / Technique:** `Security - Rate Limiting & Account Lockout`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** Registered user account exists
* **Test Data:** `Email: test_qa@example.com, Invalid Passwords x5`
* **Steps to Execute:**
  1. Enter valid email and incorrect password 5 times consecutively.
  2. Click 'Login' on each attempt.
* **Expected Result:** System triggers rate limiting, temporarily locking account or requiring CAPTCHA verification.
* **Actual Result:** Account temporarily throttled / lockout warning displayed after 5 consecutive failures.

---

#### 🛠️ TC-LOG-010: Verify reset password request functionality
* **Module:** Login & Logout
* **Priority:** `Medium (P2)` | **Type / Technique:** `Functional - Password Recovery Flow`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the Login page
* **Test Data:** `Email: test_qa@example.com`
* **Steps to Execute:**
  1. Click 'Forgot your password?' link.
  2. Enter registered email address.
  3. Click 'Send Reset Link'.
* **Expected Result:** Confirmation notice indicates password reset instructions have been sent to the user email.
* **Actual Result:** Password reset instruction link sent to registered email address successfully.

---

### 📂 Module: Product Catalog & Search

#### 🛠️ TC-CAT-001: Verify navigation to Product page and product list rendering
* **Module:** Product Catalog & Search
* **Priority:** `High (P1)` | **Type / Technique:** `Functional - Catalog Rendering & Pagination`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the homepage
* **Test Data:** `URL: https://automationexercise.com/products`
* **Steps to Execute:**
  1. Click on 'Products' button in header navigation.
  2. Verify the page URL and product grid display.
* **Expected Result:** User is navigated to ALL PRODUCTS page; catalog grid displays product cards with image, price, and title.
* **Actual Result:** Product grid renders 34 products with images, titles, pricing, and Add to Cart buttons.

---

#### 🛠️ TC-CAT-002: Search for a product using exact matching product name
* **Module:** Product Catalog & Search
* **Priority:** `High (P1)` | **Type / Technique:** `Functional - Search (Exact Match)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the Products page
* **Test Data:** `Search term: 'Blue Top'`
* **Steps to Execute:**
  1. Enter 'Blue Top' into search input field.
  2. Click search icon/button.
* **Expected Result:** 'SEARCHED PRODUCTS' section displays product 'Blue Top' matching the search criteria.
* **Actual Result:** Search returns exact match 'Blue Top'; item count matches database record.

---

#### 🛠️ TC-CAT-003: Search for a product using partial match query
* **Module:** Product Catalog & Search
* **Priority:** `Medium (P2)` | **Type / Technique:** `Functional - Search (Partial Match / EP)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the Products page
* **Test Data:** `Search term: 'dress'`
* **Steps to Execute:**
  1. Enter 'dress' in the search input.
  2. Click search button.
* **Expected Result:** All products containing 'dress' in their title or description are displayed in search results.
* **Actual Result:** Partial query 'dress' returns all matching items in Women and Kids categories.

---

#### 🛠️ TC-CAT-004: Search for a product with non-existent keyword
* **Module:** Product Catalog & Search
* **Priority:** `Medium (P2)` | **Type / Technique:** `Functional - Search (Negative / Zero Results)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the Products page
* **Test Data:** `Search term: 'XYZNonExistentItem999'`
* **Steps to Execute:**
  1. Enter 'XYZNonExistentItem999' in search box.
  2. Click search button.
* **Expected Result:** Page displays a graceful empty state message indicating zero results found.
* **Actual Result:** Empty state message displayed: 'No products found matching your search criteria'.

---

#### 🛠️ TC-CAT-005: Search for a product using special characters
* **Module:** Product Catalog & Search
* **Priority:** `High (P1)` | **Type / Technique:** `Security & Error Handling (Special Chars / EP)`
* **Execution Status:** 🟥 **FAIL** (Ref: BUG-004)
* **Preconditions:** User is on the Products page
* **Test Data:** `Search term: '%', '&', '<script>'`
* **Steps to Execute:**
  1. Enter symbol '%' into search input.
  2. Click search button.
* **Expected Result:** Application handles input gracefully, sanitizes URL parameters, and displays zero results without crashing.
* **Actual Result:** Application throws unhandled HTTP 500 error or raw URL decoding server crash.
* **Linked Defect:** [BUG-004](bug-reports.md#bug-004)

---

#### 🛠️ TC-CAT-006: Verify category filtering displays correct matching items
* **Module:** Product Catalog & Search
* **Priority:** `High (P1)` | **Type / Technique:** `Functional - Taxonomy & Category Filtering`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the Products page
* **Test Data:** `Category: Women > Subcategory: Dress`
* **Steps to Execute:**
  1. In the sidebar under 'Category', click 'Women'.
  2. Click 'Dress' link under Women subcategory.
* **Expected Result:** User is redirected to category page; page title shows 'WOMEN - DRESS PRODUCTS'; only matching items display.
* **Actual Result:** Selecting 'Women > Dress' filters catalog to 3 relevant dress products.

---

#### 🛠️ TC-CAT-007: Verify category filtering works correctly on mobile viewports
* **Module:** Product Catalog & Search
* **Priority:** `High (P1)` | **Type / Technique:** `Compatibility & Mobile Responsive UI`
* **Execution Status:** 🟥 **FAIL** (Ref: BUG-005)
* **Preconditions:** Website accessed on mobile viewport (e.g., iPhone Safari / Chrome DevTools 390px)
* **Test Data:** `Viewport: 390x844 (iPhone 14 Safari)`
* **Steps to Execute:**
  1. Access website on mobile viewport.
  2. Tap 'Women' category accordion.
  3. Tap 'Dress' subcategory link.
* **Expected Result:** Accordion expands smoothly; tapping 'Dress' redirects viewport to Women-Dress catalog.
* **Actual Result:** Tapping expands the category menu but instantly collapses it without executing page redirection.
* **Linked Defect:** [BUG-005](bug-reports.md#bug-005)

---

#### 🛠️ TC-CAT-008: Verify viewing details of a specific product
* **Module:** Product Catalog & Search
* **Priority:** `High (P1)` | **Type / Technique:** `Functional - Product Details & SKU View`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the Products page
* **Test Data:** `Product: 'Blue Top' (Product ID: 1)`
* **Steps to Execute:**
  1. Click 'View Product' button for 'Blue Top'.
  2. Inspect details screen.
* **Expected Result:** Product details page opens displaying: Product Name, Category, Price, Availability, Condition, Brand, and Quantity box.
* **Actual Result:** Product detail page displays high-res image, SKU, category, price ($500), condition, and stock status.

---

#### 🛠️ TC-CAT-009: Verify brand sidebar filters products correctly
* **Module:** Product Catalog & Search
* **Priority:** `Medium (P2)` | **Type / Technique:** `Functional - Brand Facet Filtering`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the Products page
* **Test Data:** `Brand: 'Polo'`
* **Steps to Execute:**
  1. Under Brands sidebar, click 'Polo'.
  2. Verify displayed items.
* **Expected Result:** URL reflects brand filter; only products manufactured by 'Polo' brand are displayed.
* **Actual Result:** Clicking 'Polo' brand filters listing to display only Polo-branded apparel.

---

#### 🛠️ TC-CAT-010: Verify 'Back to Products' link on details page returns to previous list state
* **Module:** Product Catalog & Search
* **Priority:** `Low (P3)` | **Type / Technique:** `UI / State Preservation & Navigation`
* **Execution Status:** 🟥 **FAIL** (Ref: BUG-006)
* **Preconditions:** User has applied 'Polo' brand filter and clicked into a product detail page
* **Test Data:** `Filter: Brand 'Polo' -> Detail View -> Back Button`
* **Steps to Execute:**
  1. Navigate to Products, filter by 'Polo' brand.
  2. Click 'View Product'.
  3. Click 'Back to Products' button on detail page.
* **Expected Result:** User returns to filtered Polo brand catalog view.
* **Actual Result:** User is redirected to the main store root homepage, losing the active brand filter configuration.
* **Linked Defect:** [BUG-006](bug-reports.md#bug-006)

---

### 📂 Module: Shopping Cart & Cart Actions

#### 🛠️ TC-CRT-001: Add a single product to cart from Products list
* **Module:** Shopping Cart & Cart Actions
* **Priority:** `High (P1)` | **Type / Technique:** `Functional - Positive (Cart Addition)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the Products page
* **Test Data:** `Product: 'Blue Top', Quantity: 1`
* **Steps to Execute:**
  1. Hover over first product 'Blue Top'.
  2. Click 'Add to cart'.
  3. Click 'Continue Shopping' on the modal.
* **Expected Result:** Product is added to cart; confirmation modal appears; header cart badge updates.
* **Actual Result:** Modal confirms 'Your product has been added to cart'; cart count increments by 1.

---

#### 🛠️ TC-CRT-002: Add multiple products to cart and verify details
* **Module:** Shopping Cart & Cart Actions
* **Priority:** `High (P1)` | **Type / Technique:** `Functional - Positive (Multi-item Cart)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the Products page
* **Test Data:** `Product 1: 'Blue Top' ($500), Product 2: 'Men Tshirt' ($400)`
* **Steps to Execute:**
  1. Add 'Blue Top' to cart.
  2. Add 'Men Tshirt' to cart.
  3. Click 'View Cart'.
* **Expected Result:** Both items are displayed in cart with exact price, quantity 1, and correct itemized subtotals.
* **Actual Result:** Cart table displays both items with correct titles, unit prices, quantities, and line subtotals.

---

#### 🛠️ TC-CRT-003: Add same product multiple times and verify quantity increment
* **Module:** Shopping Cart & Cart Actions
* **Priority:** `High (P1)` | **Type / Technique:** `Business Logic - Cart Accumulation`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on the Products page
* **Test Data:** `Product: 'Blue Top' added twice`
* **Steps to Execute:**
  1. Click 'Add to cart' on 'Blue Top'.
  2. Click 'Continue Shopping'.
  3. Click 'Add to cart' on 'Blue Top' again.
  4. Open Cart page.
* **Expected Result:** 'Blue Top' row displays quantity = 2, and subtotal equals 2 x Unit Price.
* **Actual Result:** Adding existing cart item increments quantity to 2; unit price unchanged; subtotal doubles.

---

#### 🛠️ TC-CRT-004: Verify add is blocked for zero-stock / out-of-stock items
* **Module:** Shopping Cart & Cart Actions
* **Priority:** `High (P1)` | **Type / Technique:** `Business Logic & Inventory Control`
* **Execution Status:** 🟥 **FAIL** (Ref: BUG-007)
* **Preconditions:** Product with inventory quantity = 0 exists in catalog
* **Test Data:** `Product: Out of Stock item (Stock = 0)`
* **Steps to Execute:**
  1. Search for out-of-stock product.
  2. Hover over product card.
  3. Click 'Add to Cart' button.
* **Expected Result:** Button is disabled or shows 'Out of Stock' alert; item cannot be added to cart.
* **Actual Result:** Product is added to the cart successfully via hover overlay, allowing purchase of unfulfillable inventory.
* **Linked Defect:** [BUG-007](bug-reports.md#bug-007)

---

#### 🛠️ TC-CRT-005: Modify quantity directly in product details before adding
* **Module:** Shopping Cart & Cart Actions
* **Priority:** `Medium (P2)` | **Type / Technique:** `Boundary Value Analysis (BVA - Quantity)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on Product Details page for 'Blue Top'
* **Test Data:** `Quantity: 4`
* **Steps to Execute:**
  1. Change quantity input value to '4'.
  2. Click 'Add to cart' button.
  3. Navigate to Cart view.
* **Expected Result:** Cart displays 'Blue Top' with exact quantity of 4 and total price calculated accordingly.
* **Actual Result:** Setting quantity to 4 on details page adds 4 units to cart in a single action.

---

#### 🛠️ TC-CRT-006: Verify negative or zero quantities are blocked in cart input
* **Module:** Shopping Cart & Cart Actions
* **Priority:** `High (P1)` | **Type / Technique:** `Boundary Value Analysis (BVA - Negative / Zero)`
* **Execution Status:** 🟥 **FAIL** (Ref: BUG-008)
* **Preconditions:** Item is present in shopping cart
* **Test Data:** `Quantity inputs: -2, 0`
* **Steps to Execute:**
  1. In Cart view, click quantity field for item.
  2. Type '-2' and hit Enter or submit.
* **Expected Result:** Input validation resets value to 1 or displays error; total cannot become negative.
* **Actual Result:** Cart row total and cart grand total recalculate to a negative currency balance (e.g. -$58.00).
* **Linked Defect:** [BUG-008](bug-reports.md#bug-008)

---

#### 🛠️ TC-CRT-007: Remove an item from cart using the 'X' button
* **Module:** Shopping Cart & Cart Actions
* **Priority:** `Medium (P2)` | **Type / Technique:** `UI / Event Handling & Cart Removal`
* **Execution Status:** 🟥 **FAIL** (Ref: BUG-009)
* **Preconditions:** Cart contains 1 or more items
* **Test Data:** `Product row in Cart`
* **Steps to Execute:**
  1. Navigate to Cart page.
  2. Click the red 'X' delete button once for the item row.
* **Expected Result:** Item is removed immediately from cart table on a single click; totals recalculate.
* **Actual Result:** Row remains active on initial click; requires double-clicking the button to execute removal.
* **Linked Defect:** [BUG-009](bug-reports.md#bug-009)

---

#### 🛠️ TC-CRT-008: Verify cart count badge in header updates dynamically
* **Module:** Shopping Cart & Cart Actions
* **Priority:** `Medium (P2)` | **Type / Technique:** `UI / Reactive State (Badge Counter)`
* **Execution Status:** 🟥 **FAIL** (Ref: BUG-010)
* **Preconditions:** Cart contains 2 items (header badge shows '2')
* **Test Data:** `2 items in Cart -> delete 1 item`
* **Steps to Execute:**
  1. Navigate to Cart page.
  2. Delete one item from cart table.
* **Expected Result:** Header cart badge count decrements dynamically to '1' without requiring full page reload.
* **Actual Result:** Header badge count remains '2' until a manual browser refresh is performed.
* **Linked Defect:** [BUG-010](bug-reports.md#bug-010)

---

#### 🛠️ TC-CRT-009: Verify cart persistence across logout/login sessions
* **Module:** Shopping Cart & Cart Actions
* **Priority:** `High (P1)` | **Type / Technique:** `Session Management & Cart Persistence`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is logged in
* **Test Data:** `User account with 2 items in Cart`
* **Steps to Execute:**
  1. Add items to cart while logged in.
  2. Log out of account.
  3. Log back in with the same account credentials.
  4. Check Cart.
* **Expected Result:** Items previously added remain in the user cart across sessions.
* **Actual Result:** Cart contents remain intact in session storage / database after logout and re-login.

---

#### 🛠️ TC-CRT-010: Verify subtotal and grand total update automatically on quantity change
* **Module:** Shopping Cart & Cart Actions
* **Priority:** `High (P1)` | **Type / Technique:** `Business Logic & Calculation Engine`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** Cart contains items
* **Test Data:** `Item 1: $500 x 2 = $1000, Item 2: $400 x 1 = $400, Total = $1400`
* **Steps to Execute:**
  1. Add 2 units of Item 1 and 1 unit of Item 2 to cart.
  2. Navigate to Cart page.
  3. Verify individual totals and grand total sum.
* **Expected Result:** Total sum mathematically equals the sum of line subtotals ($1400.00).
* **Actual Result:** Subtotal and order grand total dynamically update without page refresh upon quantity change.

---

### 📂 Module: Checkout, Billing & Payments

#### 🛠️ TC-CHK-001: Verify checkout navigation for logged-in user
* **Module:** Checkout, Billing & Payments
* **Priority:** `High (P1)` | **Type / Technique:** `Functional - Positive (Checkout Navigation)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is logged in and has items in cart
* **Test Data:** `Cart with 1 item, logged-in session`
* **Steps to Execute:**
  1. Navigate to Cart page.
  2. Click 'Proceed To Checkout' button.
* **Expected Result:** User is directed to the Checkout page displaying Address Details and Order Review.
* **Actual Result:** Logged-in user clicking 'Proceed to Checkout' navigates directly to order review page.

---

#### 🛠️ TC-CHK-002: Verify Address Details page displays correct default user details
* **Module:** Checkout, Billing & Payments
* **Priority:** `High (P1)` | **Type / Technique:** `Data Integrity & Profile Auto-fill`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is at Checkout step
* **Test Data:** `User registered address: 123 Automation Blvd, Los Angeles, CA 90001`
* **Steps to Execute:**
  1. Review 'YOUR DELIVERY ADDRESS' and 'YOUR BILLING ADDRESS' sections.
* **Expected Result:** Both addresses accurately match the details entered during user account registration.
* **Actual Result:** Delivery Address and Billing Address auto-populated matching user profile registration data.

---

#### 🛠️ TC-CHK-003: Verify user can add comments/notes to order
* **Module:** Checkout, Billing & Payments
* **Priority:** `Low (P3)` | **Type / Technique:** `Functional - Order Notes / Comments`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on Checkout page
* **Test Data:** `Comment: 'Please deliver between 9 AM and 5 PM on weekdays.'`
* **Steps to Execute:**
  1. Scroll down to comment textarea.
  2. Enter order comment.
  3. Click 'Place Order'.
* **Expected Result:** Order comment is saved and associated with the placed order in database.
* **Actual Result:** Order comment field accepts 250 characters and attaches to order summary payload.

---

#### 🛠️ TC-CHK-004: Verify Payment page details input masking
* **Module:** Checkout, Billing & Payments
* **Priority:** `Medium (P2)` | **Type / Technique:** `UI / Security (Payment Form Masking)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on Payment page (https://automationexercise.com/payment)
* **Test Data:** `CVV: '311', Card: '4111 2222 3333 4444'`
* **Steps to Execute:**
  1. Input CVV code into CVV field.
  2. Inspect field rendering.
* **Expected Result:** CVV digits are masked with bullet characters or password styling for sensitive financial privacy.
* **Actual Result:** CVV field masked with dots; Card Number formatted with 4-digit spacing.

---

#### 🛠️ TC-CHK-005: Verify place order with valid promo code discounts price
* **Module:** Checkout, Billing & Payments
* **Priority:** `High (P1)` | **Type / Technique:** `Business Logic & Promo Code Engine`
* **Execution Status:** 🟥 **FAIL** (Ref: BUG-011)
* **Preconditions:** User is on Checkout review page with order total $100.00
* **Test Data:** `Promo Code: 'DISCOUNT10' (intended 10% discount)`
* **Steps to Execute:**
  1. Enter promo code 'DISCOUNT10' into coupon input box.
  2. Click 'Apply' button.
* **Expected Result:** Subtotal is reduced by 10% ($10.00 discount); new total reflects $90.00.
* **Actual Result:** Promo code deducts 100% of the entire order value ($0.00 balance due), allowing items for free.
* **Linked Defect:** [BUG-011](bug-reports.md#bug-011)

---

#### 🛠️ TC-CHK-006: Verify checkout button is active and functional in all major browsers
* **Module:** Checkout, Billing & Payments
* **Priority:** `High (P1)` | **Type / Technique:** `Cross-Browser Compatibility`
* **Execution Status:** 🟥 **FAIL** (Ref: BUG-012)
* **Preconditions:** Checkout page accessed on Mozilla Firefox browser
* **Test Data:** `Browser: Mozilla Firefox v120+, Checkout page`
* **Steps to Execute:**
  1. Access checkout page in Firefox.
  2. Fill comments and scroll to bottom.
  3. Click 'Place Order' button.
* **Expected Result:** 'Place Order' button is enabled and clickable across all supported browsers.
* **Actual Result:** Button remains permanently disabled in Firefox due to an unhandled CSS/JS event discrepancy.
* **Linked Defect:** [BUG-012](bug-reports.md#bug-012)

---

#### 🛠️ TC-CHK-007: Pay using credit card with 2-digit expiration year
* **Module:** Checkout, Billing & Payments
* **Priority:** `High (P1)` | **Type / Technique:** `Boundary & Format Validation (BVA - Date)`
* **Execution Status:** 🟥 **FAIL** (Ref: BUG-013)
* **Preconditions:** User is on Payment screen
* **Test Data:** `Card: 4111222233334444, CVV: 123, Month: 12, Year: '28' (2-digit)`
* **Steps to Execute:**
  1. Enter valid card number, name, CVV, month 12.
  2. In Expiration Year field, type '28'.
  3. Click 'Pay and Confirm Order'.
* **Expected Result:** System validates format and normalizes to '2028' or alerts user to enter 4 digits without crashing.
* **Actual Result:** Page crashes with an unhandled backend server exception: DateTimeParseException: Year must be 4 digits.
* **Linked Defect:** [BUG-013](bug-reports.md#bug-013)

---

#### 🛠️ TC-CHK-008: Pay using credit card with standard valid parameters
* **Module:** Checkout, Billing & Payments
* **Priority:** `High (P1)` | **Type / Technique:** `Functional - Positive (End-to-End Payment)`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on Payment screen
* **Test Data:** `Card: 4111222233334444, CVV: 311, Exp: 12/2028, Name: John Doe`
* **Steps to Execute:**
  1. Fill Name on Card, Card Number, CVV, Expiration Month, and 4-digit Year.
  2. Click 'Pay and Confirm Order'.
* **Expected Result:** Payment processes successfully; 'ORDER PLACED!' confirmation screen is displayed.
* **Actual Result:** Valid payment processed; order confirmation screen displayed with unique Order ID #ORD-9821.

---

#### 🛠️ TC-CHK-009: Verify Tax/VAT calculations are correct on order breakdown
* **Module:** Checkout, Billing & Payments
* **Priority:** `High (P1)` | **Type / Technique:** `Business Logic & Financial Calculations`
* **Execution Status:** 🟥 **FAIL** (Ref: BUG-014)
* **Preconditions:** User is reviewing checkout order totals with subtotal $10.00
* **Test Data:** `Subtotal: $10.00, Standard Tax Rate: 10% ($1.00)`
* **Steps to Execute:**
  1. Add a $10.00 item to cart and proceed to checkout review.
  2. Check the Tax calculation row.
* **Expected Result:** Tax line displays exactly $1.00 according to standard 10% tax rate policy.
* **Actual Result:** Tax line displays $2.50, arbitrarily applying an incorrect flat 25% tax rate without documentation.
* **Linked Defect:** [BUG-014](bug-reports.md#bug-014)

---

#### 🛠️ TC-CHK-010: Verify order confirmation screen displays Invoice Download link
* **Module:** Checkout, Billing & Payments
* **Priority:** `Medium (P2)` | **Type / Technique:** `Functional - Order Completion & Invoice Link`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** Order has been successfully placed
* **Test Data:** `Order Confirmation page`
* **Steps to Execute:**
  1. Inspect Order Placed screen elements.
* **Expected Result:** 'Download Invoice' button and 'Continue' button are visible and active.
* **Actual Result:** 'Download Invoice' button rendered cleanly on order confirmation page.

---

#### 🛠️ TC-CHK-011: Verify Download Invoice option outputs valid document
* **Module:** Checkout, Billing & Payments
* **Priority:** `Medium (P2)` | **Type / Technique:** `Functional - File Download & PDF Verification`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on Order Confirmation page
* **Test Data:** `Download Invoice Action`
* **Steps to Execute:**
  1. Click 'Download Invoice' button.
  2. Check browser downloads.
* **Expected Result:** A valid invoice file (.txt/.pdf) containing order number, items, and total price is downloaded to client disk.
* **Actual Result:** Clicking 'Download Invoice' generates and downloads valid PDF invoice file.

---

#### 🛠️ TC-CHK-012: Verify order confirmation email formatting
* **Module:** Checkout, Billing & Payments
* **Priority:** `Low (P3)` | **Type / Technique:** `Integration & Email Template Rendering`
* **Execution Status:** 🟥 **FAIL** (Ref: BUG-015)
* **Preconditions:** Order placed successfully by registered user
* **Test Data:** `Email recipient: test_qa@example.com`
* **Steps to Execute:**
  1. Complete purchase.
  2. Open order confirmation email received in user inbox.
* **Expected Result:** Email displays nicely styled HTML table, clean branding, order ID, and product breakdown.
* **Actual Result:** Email body renders plaintext with raw HTML tags visible (e.g., 'Dear Customer, <br/> Your order <b>#1029</b>').
* **Linked Defect:** [BUG-015](bug-reports.md#bug-015)

---

### 📂 Module: General & Contact Us

#### 🛠️ TC-GEN-001: Submit Contact Us form with unsupported attachment formats
* **Module:** General & Contact Us
* **Priority:** `High (P1)` | **Type / Technique:** `Security & File Upload Validation (EP)`
* **Execution Status:** 🟥 **FAIL** (Ref: BUG-016)
* **Preconditions:** User is on Contact Us page (https://automationexercise.com/contact_us)
* **Test Data:** `File: 'exploit_script.exe' (Executable binary)`
* **Steps to Execute:**
  1. Fill Name, Email, Subject, and Message.
  2. Click 'Choose File' and select an executable '.exe' file.
  3. Click 'Submit' button.
* **Expected Result:** File uploader rejects .exe format; inline validation restricts uploads to images/documents (.png, .jpg, .pdf).
* **Actual Result:** System accepts and uploads executable .exe file without MIME-type or extension validation.
* **Linked Defect:** [BUG-016](bug-reports.md#bug-016)

---

#### 🛠️ TC-GEN-002: Verify newsletter subscription validation
* **Module:** General & Contact Us
* **Priority:** `Low (P3)` | **Type / Technique:** `Functional - Subscription & Email Validation`
* **Execution Status:** 🟩 **PASS**
* **Preconditions:** User is on homepage footer section
* **Test Data:** `Email: valid_subscriber@example.com`
* **Steps to Execute:**
  1. Scroll down to footer.
  2. Enter valid email in 'SUBSCRIPTION' input.
  3. Click arrow submit button.
* **Expected Result:** Success message 'You have been successfully subscribed!' is displayed dynamically.
* **Actual Result:** Entering email into footer newsletter form displays success alert 'You have been successfully subscribed!'.

---

