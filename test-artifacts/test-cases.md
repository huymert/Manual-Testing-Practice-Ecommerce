# Test Cases Suite: Automation Exercise

This file contains **52 comprehensive test cases** designed and executed for the **Automation Exercise** website.
These test cases are grouped by core e-commerce modules. Failed test cases include cross-references to the logged defects in [bug-reports.md](bug-reports.md).

> [!TIP]
> You can download the spreadsheet version of this test suite in [test-cases.csv](test-cases.csv) and import it into Google Sheets, Excel, or test case management tools like TestRail.

---

## Test Cases Summary Table

| Test Case ID | Module | Title | Status |
| :--- | :--- | :--- | :--- |
| TC-REG-001 | Registration & Account Management | Register successfully with all valid required fields | ✅ **Pass** |
| TC-REG-002 | Registration & Account Management | Register successfully with all optional fields filled | ✅ **Pass** |
| TC-REG-003 | Registration & Account Management | Register with an email address that is already registered | ✅ **Pass** |
| TC-REG-004 | Registration & Account Management | Register with invalid email format | ✅ **Pass** |
| TC-REG-005 | Registration & Account Management | Register leaving required fields empty | ❌ **Fail** ([BUG-001](bug-reports.md#bug-001)) |
| TC-REG-006 | Registration & Account Management | Register with special characters / SQL syntax in Name fields | ❌ **Fail** ([BUG-002](bug-reports.md#bug-002)) |
| TC-REG-007 | Registration & Account Management | Register with password less than minimum length | ✅ **Pass** |
| TC-REG-008 | Registration & Account Management | Verify password fields hide inputs by default | ✅ **Pass** |
| TC-REG-009 | Registration & Account Management | Verify account creation immediately establishes session | ✅ **Pass** |
| TC-REG-010 | Registration & Account Management | Verify delete account functionality removes user from system | ✅ **Pass** |
| TC-LOG-001 | Login & Logout | Login successfully with valid registered credentials | ✅ **Pass** |
| TC-LOG-002 | Login & Logout | Login failed with unregistered email | ✅ **Pass** |
| TC-LOG-003 | Login & Logout | Login failed with incorrect password for registered email | ✅ **Pass** |
| TC-LOG-004 | Login & Logout | Login failed with empty email and password fields | ✅ **Pass** |
| TC-LOG-005 | Login & Logout | Verify session persistence using 'Remember me' option | ❌ **Fail** ([BUG-003](bug-reports.md#bug-003)) |
| TC-LOG-006 | Login & Logout | Verify password field toggles input visibility | ✅ **Pass** |
| TC-LOG-007 | Login & Logout | Verify successful logout terminates user session | ✅ **Pass** |
| TC-LOG-008 | Login & Logout | Verify redirection to login page when accessing checkout without authorization | ✅ **Pass** |
| TC-LOG-009 | Login & Logout | Verify account lockout after multiple failed login attempts | ✅ **Pass** |
| TC-LOG-010 | Login & Logout | Verify reset password request functionality | ✅ **Pass** |
| TC-CAT-001 | Product Catalog & Search | Verify navigation to Product page and product list rendering | ✅ **Pass** |
| TC-CAT-002 | Product Catalog & Search | Search for a product using exact matching product name | ✅ **Pass** |
| TC-CAT-003 | Product Catalog & Search | Search for a product using partial match query | ✅ **Pass** |
| TC-CAT-004 | Product Catalog & Search | Search for a product with non-existent keyword | ✅ **Pass** |
| TC-CAT-005 | Product Catalog & Search | Search for a product using special characters | ❌ **Fail** ([BUG-004](bug-reports.md#bug-004)) |
| TC-CAT-006 | Product Catalog & Search | Verify category filtering displays correct matching items | ✅ **Pass** |
| TC-CAT-007 | Product Catalog & Search | Verify category filtering works correctly on mobile viewports | ❌ **Fail** ([BUG-005](bug-reports.md#bug-005)) |
| TC-CAT-008 | Product Catalog & Search | Verify viewing details of a specific product | ✅ **Pass** |
| TC-CAT-009 | Product Catalog & Search | Verify brand sidebar filters products correctly | ✅ **Pass** |
| TC-CAT-010 | Product Catalog & Search | Verify 'Back to Products' link on details page returns to previous list state | ❌ **Fail** ([BUG-006](bug-reports.md#bug-006)) |
| TC-CRT-001 | Shopping Cart & Cart Actions | Add a single product to cart from Products list | ✅ **Pass** |
| TC-CRT-002 | Shopping Cart & Cart Actions | Add multiple products to cart and verify details | ✅ **Pass** |
| TC-CRT-003 | Shopping Cart & Cart Actions | Add same product multiple times and verify quantity increment | ✅ **Pass** |
| TC-CRT-004 | Shopping Cart & Cart Actions | Verify add is blocked for zero-stock / out-of-stock items | ❌ **Fail** ([BUG-007](bug-reports.md#bug-007)) |
| TC-CRT-005 | Shopping Cart & Cart Actions | Modify quantity directly in product details before adding | ✅ **Pass** |
| TC-CRT-006 | Shopping Cart & Cart Actions | Verify negative or zero quantities are blocked in cart input | ❌ **Fail** ([BUG-008](bug-reports.md#bug-008)) |
| TC-CRT-007 | Shopping Cart & Cart Actions | Remove an item from cart using the 'X' button | ❌ **Fail** ([BUG-009](bug-reports.md#bug-009)) |
| TC-CRT-008 | Shopping Cart & Cart Actions | Verify cart count badge in header updates dynamically | ❌ **Fail** ([BUG-010](bug-reports.md#bug-010)) |
| TC-CRT-009 | Shopping Cart & Cart Actions | Verify cart persistence across logout/login sessions | ✅ **Pass** |
| TC-CRT-010 | Shopping Cart & Cart Actions | Verify subtotal and grand total update automatically on quantity change | ✅ **Pass** |
| TC-CHK-001 | Checkout, Billing & Payments | Verify checkout navigation for logged-in user | ✅ **Pass** |
| TC-CHK-002 | Checkout, Billing & Payments | Verify Address Details page displays correct default user details | ✅ **Pass** |
| TC-CHK-003 | Checkout, Billing & Payments | Verify user can add comments/notes to order | ✅ **Pass** |
| TC-CHK-004 | Checkout, Billing & Payments | Verify Payment page details input masking | ✅ **Pass** |
| TC-CHK-005 | Checkout, Billing & Payments | Verify place order with valid promo code discounts price | ❌ **Fail** ([BUG-011](bug-reports.md#bug-011)) |
| TC-CHK-006 | Checkout, Billing & Payments | Verify checkout button is active and functional in all major browsers | ❌ **Fail** ([BUG-012](bug-reports.md#bug-012)) |
| TC-CHK-007 | Checkout, Billing & Payments | Pay using credit card with 2-digit expiration year | ❌ **Fail** ([BUG-013](bug-reports.md#bug-013)) |
| TC-CHK-008 | Checkout, Billing & Payments | Pay using credit card with standard valid parameters | ✅ **Pass** |
| TC-CHK-009 | Checkout, Billing & Payments | Verify Tax/VAT calculations are correct on order breakdown | ❌ **Fail** ([BUG-014](bug-reports.md#bug-014)) |
| TC-CHK-010 | Checkout, Billing & Payments | Verify order confirmation screen displays Invoice Download link | ✅ **Pass** |
| TC-CHK-011 | Checkout, Billing & Payments | Verify Download Invoice option outputs valid document | ✅ **Pass** |
| TC-CHK-012 | Checkout, Billing & Payments | Verify order confirmation email formatting | ❌ **Fail** ([BUG-015](bug-reports.md#bug-015)) |
| TC-GEN-001 | General & Contact Us | Submit Contact Us form with unsupported attachment formats | ❌ **Fail** ([BUG-016](bug-reports.md#bug-016)) |
| TC-GEN-002 | General & Contact Us | Verify newsletter subscription validation | ✅ **Pass** |

---

## Detailed Test Cases Specification


### 📂 Module: Registration & Account Management

#### 🛠️ TC-REG-001: Register successfully with all valid required fields
*   **Module:** Registration & Account Management
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on the Signup page (https://automationexercise.com/login)
*   **Steps to Reproduce / Execute:**
    1. Enter valid Name and Email in the Signup section.
    2. Click 'Signup' button.
    3. Complete the 'Enter Account Information' form (Password, First Name, Last Name, Address, State, City, Zipcode, Mobile Number).
    4. Click 'Create Account' button.
*   **Expected Result:** Account is created successfully, user is logged in automatically, and 'ACCOUNT CREATED!' page is displayed.

---
#### 🛠️ TC-REG-002: Register successfully with all optional fields filled
*   **Module:** Registration & Account Management
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on the Signup page
*   **Steps to Reproduce / Execute:**
    1. Enter valid Name and Email and click 'Signup'.
    2. Fill all mandatory fields.
    3. Fill optional fields: Title, Date of Birth, Newsletter checkbox, Special offers checkbox, Company, Address 2.
    4. Click 'Create Account'.
*   **Expected Result:** Account is created successfully with all profile details saved correctly.

---
#### 🛠️ TC-REG-003: Register with an email address that is already registered
*   **Module:** Registration & Account Management
*   **Status:** 🟩 **PASS**
*   **Preconditions:** An account with email 'existing_user@example.com' already exists.
*   **Steps to Reproduce / Execute:**
    1. Enter Name and 'existing_user@example.com' in the Signup section.
    2. Click 'Signup' button.
*   **Expected Result:** Form submission is blocked, and validation message 'Email Address already exist!' is displayed.

---
#### 🛠️ TC-REG-004: Register with invalid email format
*   **Module:** Registration & Account Management
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on the Signup page
*   **Steps to Reproduce / Execute:**
    1. Enter Name and invalid email formats (e.g. 'user@', 'user@domain', 'user.domain.com').
    2. Click 'Signup' button.
*   **Expected Result:** HTML5 validation error blocks form submission, requiring an '@' and a valid domain format.

---
#### 🛠️ TC-REG-005: Register leaving required fields empty
*   **Module:** Registration & Account Management
*   **Status:** 🟥 **FAIL** (Refer to Defect: [BUG-001](bug-reports.md#bug-001))
*   **Preconditions:** User is on the Signup page
*   **Steps to Reproduce / Execute:**
    1. Enter Name and valid Email and click 'Signup'.
    2. On the Account details page, leave mandatory fields (Password, First Name, Last Name) empty.
    3. Click 'Create Account' button.
*   **Expected Result:** Form validation triggers indicating empty fields; page remains on details form and does not submit to server.

---
#### 🛠️ TC-REG-006: Register with special characters / SQL syntax in Name fields
*   **Module:** Registration & Account Management
*   **Status:** 🟥 **FAIL** (Refer to Defect: [BUG-002](bug-reports.md#bug-002))
*   **Preconditions:** User is on the Signup page
*   **Steps to Reproduce / Execute:**
    1. Enter a name containing quotes and database injection syntax (e.g., `' OR '1'='1`) in 'First Name' or 'Last Name'.
    2. Fill other required fields.
    3. Click 'Create Account'.
*   **Expected Result:** Input is properly sanitized. Account is created, or a validation error prevents database syntax execution. No raw SQL errors are shown.

---
#### 🛠️ TC-REG-007: Register with password less than minimum length
*   **Module:** Registration & Account Management
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on the Signup page
*   **Steps to Reproduce / Execute:**
    1. Enter valid Name and Email and click 'Signup'.
    2. Input a password of 1 character.
    3. Click 'Create Account'.
*   **Expected Result:** Validation error is displayed indicating password must be at least 6 characters.

---
#### 🛠️ TC-REG-008: Verify password fields hide inputs by default
*   **Module:** Registration & Account Management
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on the details signup form
*   **Steps to Reproduce / Execute:**
    1. Type text into the Password field.
*   **Expected Result:** Characters typed are masked as dots or asterisks for privacy.

---
#### 🛠️ TC-REG-009: Verify account creation immediately establishes session
*   **Module:** Registration & Account Management
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is filling the account creation form
*   **Steps to Reproduce / Execute:**
    1. Fill all required fields.
    2. Click 'Create Account'.
    3. Click 'Continue' on the Account Created page.
*   **Expected Result:** Logged-in session is active, and header displays 'Logged in as [Username]'.

---
#### 🛠️ TC-REG-010: Verify delete account functionality removes user from system
*   **Module:** Registration & Account Management
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is logged in
*   **Steps to Reproduce / Execute:**
    1. Click 'Delete Account' link in the header menu.
    2. Confirm account deletion.
    3. Try logging in again with the deleted credentials.
*   **Expected Result:** Account is deleted. Header shows 'ACCOUNT DELETED!'. Re-login attempt fails with incorrect credentials.

---

### 📂 Module: Login & Logout

#### 🛠️ TC-LOG-001: Login successfully with valid registered credentials
*   **Module:** Login & Logout
*   **Status:** 🟩 **PASS**
*   **Preconditions:** A registered user exists (test_qa@example.com / Password123)
*   **Steps to Reproduce / Execute:**
    1. Navigate to Login page.
    2. Enter 'test_qa@example.com' in the Login email field.
    3. Enter 'Password123' in the password field.
    4. Click 'Login' button.
*   **Expected Result:** User is redirected to the home page, and header displays 'Logged in as [Name]'.

---
#### 🛠️ TC-LOG-002: Login failed with unregistered email
*   **Module:** Login & Logout
*   **Status:** 🟩 **PASS**
*   **Preconditions:** Email 'not_registered@example.com' does not exist in system
*   **Steps to Reproduce / Execute:**
    1. Navigate to Login page.
    2. Enter 'not_registered@example.com' and password 'Password123'.
    3. Click 'Login'.
*   **Expected Result:** Login fails. Error message 'Your email or password is incorrect!' is displayed.

---
#### 🛠️ TC-LOG-003: Login failed with incorrect password for registered email
*   **Module:** Login & Logout
*   **Status:** 🟩 **PASS**
*   **Preconditions:** Registered email exists (test_qa@example.com)
*   **Steps to Reproduce / Execute:**
    1. Navigate to Login page.
    2. Enter 'test_qa@example.com' and incorrect password 'WrongPassword'.
    3. Click 'Login'.
*   **Expected Result:** Login fails. Error message 'Your email or password is incorrect!' is displayed.

---
#### 🛠️ TC-LOG-004: Login failed with empty email and password fields
*   **Module:** Login & Logout
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on the Login page
*   **Steps to Reproduce / Execute:**
    1. Leave email and password fields empty.
    2. Click 'Login'.
*   **Expected Result:** HTML5 validation message is displayed on empty fields, blocking form submission.

---
#### 🛠️ TC-LOG-005: Verify session persistence using 'Remember me' option
*   **Module:** Login & Logout
*   **Status:** 🟥 **FAIL** (Refer to Defect: [BUG-003](bug-reports.md#bug-003))
*   **Preconditions:** User is on the Login page
*   **Steps to Reproduce / Execute:**
    1. Enter valid email and password.
    2. Check the 'Remember me' / session persist checkbox (if present) and log in.
    3. Close the browser window.
    4. Open browser again and navigate to homepage.
*   **Expected Result:** User remains logged in without being prompted to login again.

---
#### 🛠️ TC-LOG-006: Verify password field toggles input visibility
*   **Module:** Login & Logout
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on the Login page
*   **Steps to Reproduce / Execute:**
    1. Enter password 'Password123' in the password field.
    2. Click on the eye/toggle icon (if available) to show password.
    3. Click it again to hide.
*   **Expected Result:** First click reveals password characters as plain text; second click masks them again.

---
#### 🛠️ TC-LOG-007: Verify successful logout terminates user session
*   **Module:** Login & Logout
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is logged in and on the homepage
*   **Steps to Reproduce / Execute:**
    1. Click 'Logout' link in the header menu.
    2. Click browser 'Back' button.
*   **Expected Result:** User is redirected to the login page. Clicking Back does not restore the logged-in session, and private pages are inaccessible.

---
#### 🛠️ TC-LOG-008: Verify redirection to login page when accessing checkout without authorization
*   **Module:** Login & Logout
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is guest (not logged in) and has products in cart
*   **Steps to Reproduce / Execute:**
    1. Navigate to Cart page.
    2. Click 'Proceed To Checkout' button.
*   **Expected Result:** A modal popup appears requiring user to 'Register / Login' to proceed to checkout.

---
#### 🛠️ TC-LOG-009: Verify account lockout after multiple failed login attempts
*   **Module:** Login & Logout
*   **Status:** 🟩 **PASS**
*   **Preconditions:** Registered account exists
*   **Steps to Reproduce / Execute:**
    1. Enter valid email and incorrect password 5 times consecutively.
*   **Expected Result:** System temporarily locks the account or displays a Captcha challenge to prevent brute force attacks.

---
#### 🛠️ TC-LOG-010: Verify reset password request functionality
*   **Module:** Login & Logout
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on the Login page
*   **Steps to Reproduce / Execute:**
    1. Click 'Forgot Password' or similar reset link.
    2. Enter registered email address.
    3. Click 'Submit'.
*   **Expected Result:** System displays confirmation that a password reset link has been sent to the email address.

---

### 📂 Module: Product Catalog & Search

#### 🛠️ TC-CAT-001: Verify navigation to Product page and product list rendering
*   **Module:** Product Catalog & Search
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on homepage
*   **Steps to Reproduce / Execute:**
    1. Click 'Products' link in the header menu.
    2. Scroll down to verify product cards are loaded.
*   **Expected Result:** User is redirected to 'ALL PRODUCTS' page. Products list displays image, title, price, and 'Add to cart' buttons.

---
#### 🛠️ TC-CAT-002: Search for a product using exact matching product name
*   **Module:** Product Catalog & Search
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on Products page. Target product 'Blue Top' exists.
*   **Steps to Reproduce / Execute:**
    1. Enter 'Blue Top' in the search input field.
    2. Click the search button/icon.
*   **Expected Result:** Products page reload displays 'SEARCHED PRODUCTS' title, listing 'Blue Top' as the primary result.

---
#### 🛠️ TC-CAT-003: Search for a product using partial match query
*   **Module:** Product Catalog & Search
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on Products page
*   **Steps to Reproduce / Execute:**
    1. Enter 'Dress' in the search input.
    2. Click search button.
*   **Expected Result:** All products containing the word 'Dress' (e.g. 'Sleeveless Dress', 'Fancy Green Dress') are displayed in search results.

---
#### 🛠️ TC-CAT-004: Search for a product with non-existent keyword
*   **Module:** Product Catalog & Search
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on Products page
*   **Steps to Reproduce / Execute:**
    1. Enter 'NonExistentItem123' in search input.
    2. Click search button.
*   **Expected Result:** Empty product list is displayed with a 'No products found' or similar friendly status message.

---
#### 🛠️ TC-CAT-005: Search for a product using special characters
*   **Module:** Product Catalog & Search
*   **Status:** 🟥 **FAIL** (Refer to Defect: [BUG-004](bug-reports.md#bug-004))
*   **Preconditions:** User is on Products page
*   **Steps to Reproduce / Execute:**
    1. Enter special characters (e.g., `%`, `&`, `*`, `'`) in the search input.
    2. Click search button.
*   **Expected Result:** Query is handled gracefully. Results either show empty (no match) or sanitized matches. No database error pages are shown.

---
#### 🛠️ TC-CAT-006: Verify category filtering displays correct matching items
*   **Module:** Product Catalog & Search
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on homepage or Products page. Sidebar categories are visible.
*   **Steps to Reproduce / Execute:**
    1. In the sidebar, click on 'Women' category.
    2. Click on 'Dress' sub-category.
*   **Expected Result:** Product list updates to display 'WOMEN - DRESS PRODUCTS' only, showing matching items.

---
#### 🛠️ TC-CAT-007: Verify category filtering works correctly on mobile viewports
*   **Module:** Product Catalog & Search
*   **Status:** 🟥 **FAIL** (Refer to Defect: [BUG-005](bug-reports.md#bug-005))
*   **Preconditions:** Responsive mobile viewport simulated (e.g. iPhone 12 Pro via Chrome DevTools)
*   **Steps to Reproduce / Execute:**
    1. Expand category dropdown sidebar menu on mobile layout.
    2. Click 'Men' -> 'Tshirts'.
*   **Expected Result:** Category sub-menu expands smoothly and navigates to the 'MEN - TSHIRTS PRODUCTS' page.

---
#### 🛠️ TC-CAT-008: Verify viewing details of a specific product
*   **Module:** Product Catalog & Search
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on Products list page
*   **Steps to Reproduce / Execute:**
    1. Click 'View Product' button on the first product card ('Blue Top').
*   **Expected Result:** Product details page opens. Details like Name, Category, Price, Availability, Condition, and Brand are displayed alongside the image.

---
#### 🛠️ TC-CAT-009: Verify brand sidebar filters products correctly
*   **Module:** Product Catalog & Search
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on Products page. Brands sidebar is visible.
*   **Steps to Reproduce / Execute:**
    1. Click on the 'Polo' brand link in the Brands sidebar list.
*   **Expected Result:** User is redirected to 'BRAND - POLO PRODUCTS' page, listing only Polo branded items.

---
#### 🛠️ TC-CAT-010: Verify 'Back to Products' link on details page returns to previous list state
*   **Module:** Product Catalog & Search
*   **Status:** 🟥 **FAIL** (Refer to Defect: [BUG-006](bug-reports.md#bug-006))
*   **Preconditions:** User filtered products by 'Polo' brand, then clicked 'View Product' on an item.
*   **Steps to Reproduce / Execute:**
    1. Click 'Back to Products' link / button on product details page.
*   **Expected Result:** User is returned to the filtered 'BRAND - POLO PRODUCTS' page, retaining previous filter context.

---

### 📂 Module: Shopping Cart & Cart Actions

#### 🛠️ TC-CRT-001: Add a single product to cart from Products list
*   **Module:** Shopping Cart & Cart Actions
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on Products page. Cart is empty.
*   **Steps to Reproduce / Execute:**
    1. Hover over the first product ('Blue Top').
    2. Click 'Add to cart'.
    3. Click 'Continue Shopping' in the confirmation modal.
*   **Expected Result:** Product is added. Cart count in header updates to 1. Cart status modal confirms success.

---
#### 🛠️ TC-CRT-002: Add multiple products to cart and verify details
*   **Module:** Shopping Cart & Cart Actions
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on Products page
*   **Steps to Reproduce / Execute:**
    1. Hover over Product 1 and click 'Add to cart'.
    2. Click 'Continue Shopping'.
    3. Hover over Product 2 and click 'Add to cart'.
    4. Click 'View Cart'.
*   **Expected Result:** Cart page is displayed with both products. Product names, prices, quantities, and totals match the selected items.

---
#### 🛠️ TC-CRT-003: Add same product multiple times and verify quantity increment
*   **Module:** Shopping Cart & Cart Actions
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on Products page
*   **Steps to Reproduce / Execute:**
    1. Click 'Add to cart' on 'Blue Top'.
    2. Click 'Continue Shopping'.
    3. Click 'Add to cart' on 'Blue Top' again.
    4. Click 'View Cart'.
*   **Expected Result:** Cart page shows 'Blue Top' as a single row with Quantity equal to 2, and the row total is double the single unit price.

---
#### 🛠️ TC-CRT-004: Verify add is blocked for zero-stock / out-of-stock items
*   **Module:** Shopping Cart & Cart Actions
*   **Status:** 🟥 **FAIL** (Refer to Defect: [BUG-007](bug-reports.md#bug-007))
*   **Preconditions:** An item exists in catalog with stock = 0.
*   **Steps to Reproduce / Execute:**
    1. Navigate to the detail page of the out-of-stock product.
    2. Attempt to click 'Add to Cart' button.
*   **Expected Result:** 'Add to Cart' button is disabled, or a message 'Out of stock' prevents adding the item to the cart.

---
#### 🛠️ TC-CRT-005: Modify quantity directly in product details before adding
*   **Module:** Shopping Cart & Cart Actions
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on details page of 'Blue Top'
*   **Steps to Reproduce / Execute:**
    1. Change quantity input field from 1 to 4.
    2. Click 'Add to cart' button.
    3. Click 'View Cart'.
*   **Expected Result:** Cart page shows 'Blue Top' with quantity 4 and matching price calculations.

---
#### 🛠️ TC-CRT-006: Verify negative or zero quantities are blocked in cart input
*   **Module:** Shopping Cart & Cart Actions
*   **Status:** 🟥 **FAIL** (Refer to Defect: [BUG-008](bug-reports.md#bug-008))
*   **Preconditions:** User has 1 item in the cart. User is on Cart page.
*   **Steps to Reproduce / Execute:**
    1. Click quantity field of the product.
    2. Type '-3' or '0' and press Enter.
*   **Expected Result:** Input is blocked/ignored, or resets back to 1. Quantity cannot be zero or negative.

---
#### 🛠️ TC-CRT-007: Remove an item from cart using the 'X' button
*   **Module:** Shopping Cart & Cart Actions
*   **Status:** 🟥 **FAIL** (Refer to Defect: [BUG-009](bug-reports.md#bug-009))
*   **Preconditions:** User has 1 item in cart. User is on Cart page.
*   **Steps to Reproduce / Execute:**
    1. Click the red 'X' button (Cart Delete) next to the product row.
*   **Expected Result:** The item is immediately removed from the cart page with a single click, and 'Cart is empty!' message is displayed.

---
#### 🛠️ TC-CRT-008: Verify cart count badge in header updates dynamically
*   **Module:** Shopping Cart & Cart Actions
*   **Status:** 🟥 **FAIL** (Refer to Defect: [BUG-010](bug-reports.md#bug-010))
*   **Preconditions:** User is on Cart page with 1 item.
*   **Steps to Reproduce / Execute:**
    1. Click the delete button next to the product row.
    2. Observe the cart icon/badge in the header menu.
*   **Expected Result:** The cart badge count changes from '1' to '0' dynamically without requiring a manual page refresh.

---
#### 🛠️ TC-CRT-009: Verify cart persistence across logout/login sessions
*   **Module:** Shopping Cart & Cart Actions
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is logged in. Product is in the cart.
*   **Steps to Reproduce / Execute:**
    1. Log out of the account.
    2. Log in again with the same credentials.
    3. Navigate to the Cart page.
*   **Expected Result:** The product added before logging out is still preserved in the shopping cart.

---
#### 🛠️ TC-CRT-010: Verify subtotal and grand total update automatically on quantity change
*   **Module:** Shopping Cart & Cart Actions
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User has items in the cart. User is on Cart page.
*   **Steps to Reproduce / Execute:**
    1. Change quantity of an item using increment arrows.
    2. Observe total price for the item row and cart grand total.
*   **Expected Result:** Totals recalculate and update instantly on UI.

---

### 📂 Module: Checkout, Billing & Payments

#### 🛠️ TC-CHK-001: Verify checkout navigation for logged-in user
*   **Module:** Checkout, Billing & Payments
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is logged in. Products are in cart.
*   **Steps to Reproduce / Execute:**
    1. Navigate to Cart page.
    2. Click 'Proceed To Checkout' button.
*   **Expected Result:** User is redirected to 'Checkout' page displaying delivery address details and order review tables.

---
#### 🛠️ TC-CHK-002: Verify Address Details page displays correct default user details
*   **Module:** Checkout, Billing & Payments
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is logged in. User details exist in profile.
*   **Steps to Reproduce / Execute:**
    1. Navigate to Checkout page.
    2. Compare 'Your Delivery Address' and 'Your Billing Address' text against details filled during registration.
*   **Expected Result:** Delivery and Billing address cards exactly match the profile information (Name, Company, Address, City, State, Country, Phone).

---
#### 🛠️ TC-CHK-003: Verify user can add comments/notes to order
*   **Module:** Checkout, Billing & Payments
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on Checkout page
*   **Steps to Reproduce / Execute:**
    1. Scroll down to 'Description' / comments text area.
    2. Enter text: 'Please leave package at the door'.
    3. Click 'Place Order' button.
*   **Expected Result:** Order comments are registered, and user is navigated to Payment page.

---
#### 🛠️ TC-CHK-004: Verify Payment page details input masking
*   **Module:** Checkout, Billing & Payments
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on Payment page
*   **Steps to Reproduce / Execute:**
    1. Locate credit card CVV and Card Number fields.
    2. Enter digits.
*   **Expected Result:** Digits in CVV and Card Number are masked or securely displayed according to standard e-commerce security expectations.

---
#### 🛠️ TC-CHK-005: Verify place order with valid promo code discounts price
*   **Module:** Checkout, Billing & Payments
*   **Status:** 🟥 **FAIL** (Refer to Defect: [BUG-011](bug-reports.md#bug-011))
*   **Preconditions:** User is on Checkout page. A valid promo code (e.g. 'PROMO10' for 10% off) is entered.
*   **Steps to Reproduce / Execute:**
    1. Enter promo code 'PROMO10' in the promo input.
    2. Click 'Apply'.
*   **Expected Result:** Promo code reduces checkout total by 10% correctly. Discount amount is clearly shown in price breakdown.

---
#### 🛠️ TC-CHK-006: Verify checkout button is active and functional in all major browsers
*   **Module:** Checkout, Billing & Payments
*   **Status:** 🟥 **FAIL** (Refer to Defect: [BUG-012](bug-reports.md#bug-012))
*   **Preconditions:** User is on Cart page in Firefox browser.
*   **Steps to Reproduce / Execute:**
    1. Fill in all billing and shipping requirements.
    2. Check the 'Proceed To Checkout' button status.
*   **Expected Result:** Checkout button is enabled, hover states trigger, and clicking it redirects to checkout address verification.

---
#### 🛠️ TC-CHK-007: Pay using credit card with 2-digit expiration year
*   **Module:** Checkout, Billing & Payments
*   **Status:** 🟥 **FAIL** (Refer to Defect: [BUG-013](bug-reports.md#bug-013))
*   **Preconditions:** User is on Payment page
*   **Steps to Reproduce / Execute:**
    1. Fill Name on Card and Card Number.
    2. Enter CVV: '123'.
    3. Enter Expiration MM: '12'.
    4. Enter Expiration YYYY: '28' (2-digit format instead of '2028').
    5. Click 'Pay and Confirm Order'.
*   **Expected Result:** System accepts 2-digit format or raises validation warning. No system crashes occur. Order completes successfully.

---
#### 🛠️ TC-CHK-008: Pay using credit card with standard valid parameters
*   **Module:** Checkout, Billing & Payments
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on Payment page
*   **Steps to Reproduce / Execute:**
    1. Enter valid Name, Card Number, CVV (e.g. '311'), Expiry MM ('08'), Expiry YYYY ('2030').
    2. Click 'Pay and Confirm Order'.
*   **Expected Result:** Payment succeeds. User is navigated to 'ORDER PLACED!' confirmation screen showing success message.

---
#### 🛠️ TC-CHK-009: Verify Tax/VAT calculations are correct on order breakdown
*   **Module:** Checkout, Billing & Payments
*   **Status:** 🟥 **FAIL** (Refer to Defect: [BUG-014](bug-reports.md#bug-014))
*   **Preconditions:** User is on Checkout summary review
*   **Steps to Reproduce / Execute:**
    1. Review subtotal and VAT/Tax percentages.
    2. Calculate expected tax mathematically and compare to displayed tax.
*   **Expected Result:** Displayed tax matches the calculated percentage of subtotal exactly (e.g. 10% tax on $100 should show $10.00).

---
#### 🛠️ TC-CHK-010: Verify order confirmation screen displays Invoice Download link
*   **Module:** Checkout, Billing & Payments
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User has just completed a payment
*   **Steps to Reproduce / Execute:**
    1. Check the 'ORDER PLACED!' page UI.
*   **Expected Result:** Page displays success message, 'Download Invoice' button/link, and 'Continue' button.

---
#### 🛠️ TC-CHK-011: Verify Download Invoice option outputs valid document
*   **Module:** Checkout, Billing & Payments
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is on Order Placed page
*   **Steps to Reproduce / Execute:**
    1. Click 'Download Invoice' button.
    2. Save and open the downloaded text/pdf file.
*   **Expected Result:** Invoice file downloads successfully and contains correct customer details, product rows, and final prices.

---
#### 🛠️ TC-CHK-012: Verify order confirmation email formatting
*   **Module:** Checkout, Billing & Payments
*   **Status:** 🟥 **FAIL** (Refer to Defect: [BUG-015](bug-reports.md#bug-015))
*   **Preconditions:** User successfully placed an order.
*   **Steps to Reproduce / Execute:**
    1. Open mock mail inbox connected to the test account.
    2. Locate and open the order confirmation email.
*   **Expected Result:** Email body displays clean text formatting, order summary tables, and branding graphics without unrendered raw HTML markup.

---

### 📂 Module: General & Contact Us

#### 🛠️ TC-GEN-001: Submit Contact Us form with unsupported attachment formats
*   **Module:** General & Contact Us
*   **Status:** 🟥 **FAIL** (Refer to Defect: [BUG-016](bug-reports.md#bug-016))
*   **Preconditions:** User is on Contact Us page (https://automationexercise.com/contact_us)
*   **Steps to Reproduce / Execute:**
    1. Enter Name, Email, Subject, and Message.
    2. In 'Upload File' input, select an executable file (e.g. 'malicious_test.exe').
    3. Click 'Submit' button.
    4. Click 'OK' on browser confirm popup.
*   **Expected Result:** Validation error prevents file upload of executable script extensions (.exe, .bat, etc.) to ensure server security.

---
#### 🛠️ TC-GEN-002: Verify newsletter subscription validation
*   **Module:** General & Contact Us
*   **Status:** 🟩 **PASS**
*   **Preconditions:** User is at homepage footer section
*   **Steps to Reproduce / Execute:**
    1. Scroll down to 'SUBSCRIPTION' section.
    2. Enter invalid email (e.g., 'no_at_symbol.com').
    3. Click arrow submit button.
*   **Expected Result:** Browser validation block triggers. Correct input allows success message 'You have been successfully subscribed!'.

---
