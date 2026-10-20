# Defect Tracking Log & Bug Reports: Automation Exercise

> **Testing Role:** Senior QA Engineer / QA Lead  
> **Total Defects Identified:** 16 | **Critical:** 4 | **High:** 6 | **Medium:** 3 | **Low:** 3  
> **Jira Kanban Simulation:** Active Defect Backlog

---

## 📋 Defect Summary Table

| Defect ID | Severity | Priority | Title | Module | Linked TC | Status |
| :--- | :---: | :---: | :--- | :--- | :---: | :---: |
| [BUG-001](#bug-001) | **High** | `High (P1)` | Registration detail page permits empty inputs for mandatory profile fields | Registration & Account Management | `TC-REG-005` | **Open** |
| [BUG-002](#bug-002) | **Critical** | `High (P1)` | Raw database SQL query error displayed during signup with special characters in Name field | Registration & Account Management | `TC-REG-006` | **Open** |
| [BUG-003](#bug-003) | **Medium** | `Medium (P2)` | 'Remember me' session login token is not persisted after browser restart | Login & Logout | `TC-LOG-005` | **Open** |
| [BUG-004](#bug-004) | **High** | `Medium (P2)` | Product Search page returns server error when search input contains query symbols like '%' | Product Catalog & Search | `TC-CAT-005` | **Open** |
| [BUG-005](#bug-005) | **High** | `High (P1)` | Sidebar category menu collapses and fails to navigate on iOS Safari mobile viewports | Product Catalog & Search | `TC-CAT-007` | **Open** |
| [BUG-006](#bug-006) | **Low** | `Low (P3)` | 'Back to Products' link on product details page redirects to homepage instead of filtered listing | Product Catalog & Search | `TC-CAT-010` | **Open** |
| [BUG-007](#bug-007) | **High** | `High (P1)` | Out of stock products can be added to the cart via quick hover menu | Shopping Cart & Cart Actions | `TC-CRT-004` | **Open** |
| [BUG-008](#bug-008) | **Critical** | `High (P1)` | Cart quantity input accepts negative values and recalculates total negatively | Shopping Cart & Cart Actions | `TC-CRT-006` | **Open** |
| [BUG-009](#bug-009) | **Low** | `Low (P3)` | Removing product row from cart page requires double-clicking the delete 'X' button | Shopping Cart & Cart Actions | `TC-CRT-007` | **Open** |
| [BUG-010](#bug-010) | **Medium** | `Medium (P2)` | Cart header count badge does not decrement immediately when deleting an item | Shopping Cart & Cart Actions | `TC-CRT-008` | **Open** |
| [BUG-011](#bug-011) | **Critical** | `High (P1)` | Applying a valid 10% promo code deducts 100% of order value at checkout | Checkout, Billing & Payments | `TC-CHK-005` | **Open** |
| [BUG-012](#bug-012) | **High** | `High (P1)` | Checkout confirmation button remains disabled on Firefox browsers | Checkout, Billing & Payments | `TC-CHK-006` | **Open** |
| [BUG-013](#bug-013) | **Critical** | `High (P1)` | Credit card billing page throws 500 error when expiration year is entered in 2-digit format | Checkout, Billing & Payments | `TC-CHK-007` | **Open** |
| [BUG-014](#bug-014) | **Medium** | `Medium (P2)` | Tax rate on Checkout summary matches a flat 25% instead of standard 10% tax rate | Checkout, Billing & Payments | `TC-CHK-009` | **Open** |
| [BUG-015](#bug-015) | **Low** | `Low (P3)` | Order confirmation email displays unrendered raw HTML tags in mail client | Checkout, Billing & Payments | `TC-CHK-012` | **Open** |
| [BUG-016](#bug-016) | **High** | `High (P1)` | Contact Us attachment file uploader accepts executable files (.exe) | General & Contact Us | `TC-GEN-001` | **Open** |

---

## 🐞 Detailed Defect Reports

### <a id="bug-001"></a>[BUG-001] Registration detail page permits empty inputs for mandatory profile fields

| Attribute | Specification Details |
| :--- | :--- |
| **Defect ID** | `BUG-001` |
| **Module** | Registration & Account Management |
| **Severity** | **High** |
| **Priority** | **High (P1)** |
| **Status** | **Open** |
| **Evidence Path** | `evident/bugs/BUG_001_empty_mandatory_fields.png` |
| **Linked Test Case** | `TC-REG-005` |

**Preconditions:**
User initiated signup with name and email, navigated to account details page.

**Test Data:**
`Mandatory fields: [EMPTY]`

**Steps to Reproduce:**
1. Navigate to 'https://automationexercise.com/login'.
2. Enter Name 'Test User' and Email 'new_reg_empty@test.com' under Signup, click 'Signup'.
3. Leave Password, First Name, Last Name, and Address fields completely blank.
4. Click 'Create Account'.

**Expected Result:**
Client-side and server-side validation intercept submission, highlighting missing required fields in red.

**Actual Result:**
Form successfully submits; account is created with NULL essential fields, resulting in fatal checkout profile reference errors.

---

### <a id="bug-002"></a>[BUG-002] Raw database SQL query error displayed during signup with special characters in Name field

| Attribute | Specification Details |
| :--- | :--- |
| **Defect ID** | `BUG-002` |
| **Module** | Registration & Account Management |
| **Severity** | **Critical** |
| **Priority** | **High (P1)** |
| **Status** | **Open** |
| **Evidence Path** | `evident/bugs/BUG_002_sql_injection_traceback.png` |
| **Linked Test Case** | `TC-REG-006` |

**Preconditions:**
User on signup details page.

**Test Data:**
`First Name: John' OR '1'='1`

**Steps to Reproduce:**
1. Navigate to signup details screen.
2. In 'First Name' field, input: John' OR '1'='1.
3. Complete remaining fields with valid values.
4. Click 'Create Account' button.

**Expected Result:**
Inputs are sanitized via parameterized queries before execution. User registration proceeds or handles special characters as literal text.

**Actual Result:**
Screen redirects to raw database exception traceback showing SQL query structure, exposing system to SQL Injection vulnerability.

---

### <a id="bug-003"></a>[BUG-003] 'Remember me' session login token is not persisted after browser restart

| Attribute | Specification Details |
| :--- | :--- |
| **Defect ID** | `BUG-003` |
| **Module** | Login & Logout |
| **Severity** | **Medium** |
| **Priority** | **Medium (P2)** |
| **Status** | **Open** |
| **Evidence Path** | `evident/bugs/BUG_003_session_cookie_expire.png` |
| **Linked Test Case** | `TC-LOG-005` |

**Preconditions:**
User has valid account credentials.

**Test Data:**
`Credentials: test_qa@example.com / Password123, Checkbox: Checked`

**Steps to Reproduce:**
1. Navigate to login screen, enter valid credentials, and check 'Remember me' checkmark.
2. Click 'Login' (Success).
3. Close browser completely.
4. Relaunch browser and go back to 'https://automationexercise.com'.

**Expected Result:**
Login session cookie remains active with defined expiration; header displays 'Logged in as [Name]'.

**Actual Result:**
User session is completely wiped, requiring user to log in again. Cookie is set as session-only lacking 'Max-Age' or 'Expires' header.

---

### <a id="bug-004"></a>[BUG-004] Product Search page returns server error when search input contains query symbols like '%'

| Attribute | Specification Details |
| :--- | :--- |
| **Defect ID** | `BUG-004` |
| **Module** | Product Catalog & Search |
| **Severity** | **High** |
| **Priority** | **Medium (P2)** |
| **Status** | **Open** |
| **Evidence Path** | `evident/bugs/BUG_004_search_500_error.png` |
| **Linked Test Case** | `TC-CAT-005` |

**Preconditions:**
User is on Products catalog page.

**Test Data:**
`Search Query: '%'`

**Steps to Reproduce:**
1. Navigate to 'Products' page.
2. Input symbol '%' in search field.
3. Click search button.

**Expected Result:**
Page displays zero results found gracefully without backend failure.

**Actual Result:**
Application throws unhandled HTTP 500 error or raw URL decoding server crash.

---

### <a id="bug-005"></a>[BUG-005] Sidebar category menu collapses and fails to navigate on iOS Safari mobile viewports

| Attribute | Specification Details |
| :--- | :--- |
| **Defect ID** | `BUG-005` |
| **Module** | Product Catalog & Search |
| **Severity** | **High** |
| **Priority** | **High (P1)** |
| **Status** | **Open** |
| **Evidence Path** | `evident/bugs/BUG_005_ios_category_collapse.png` |
| **Linked Test Case** | `TC-CAT-007` |

**Preconditions:**
User accessing site on touch-enabled mobile screen (<= 768px).

**Test Data:**
`Touch event on 'Women > Dress' link`

**Steps to Reproduce:**
1. Access website on iPhone Safari.
2. Scroll to Categories section.
3. Tap 'Women' to expand subcategories.
4. Tap 'Dress' subcategory link.

**Expected Result:**
Category sub-links remain expanded; tapping subcategory navigates smoothly to target page.

**Actual Result:**
Tapping expands the category menu but instantly triggers a touch-end event collapsing the accordion, preventing navigation.

---

### <a id="bug-006"></a>[BUG-006] 'Back to Products' link on product details page redirects to homepage instead of filtered listing

| Attribute | Specification Details |
| :--- | :--- |
| **Defect ID** | `BUG-006` |
| **Module** | Product Catalog & Search |
| **Severity** | **Low** |
| **Priority** | **Low (P3)** |
| **Status** | **Open** |
| **Evidence Path** | `evident/bugs/BUG_006_back_to_products_redirect.png` |
| **Linked Test Case** | `TC-CAT-010` |

**Preconditions:**
User has applied a brand/category filter prior to opening product detail.

**Test Data:**
`Active filter: Brand = 'Polo'`

**Steps to Reproduce:**
1. Navigate to Products page and click 'Polo' brand in filter sidebar.
2. Click 'View Product' for one of the filtered items.
3. Click the 'Back to Products' button on details screen.

**Expected Result:**
User returns to the filtered Polo brand catalog view.

**Actual Result:**
User is redirected to the main store homepage ('/'), losing the active brand filter configuration.

---

### <a id="bug-007"></a>[BUG-007] Out of stock products can be added to the cart via quick hover menu

| Attribute | Specification Details |
| :--- | :--- |
| **Defect ID** | `BUG-007` |
| **Module** | Shopping Cart & Cart Actions |
| **Severity** | **High** |
| **Priority** | **High (P1)** |
| **Status** | **Open** |
| **Evidence Path** | `evident/bugs/BUG_007_out_of_stock_add_cart.png` |
| **Linked Test Case** | `TC-CRT-004` |

**Preconditions:**
Product with stock_count = 0 exists in store.

**Test Data:**
`Out-of-stock SKU #14`

**Steps to Reproduce:**
1. Search for a product that is out of stock (quantity = 0).
2. Hover over the item card in product list.
3. Click the 'Add to Cart' button from the overlay.

**Expected Result:**
Hover overlay button is disabled or hidden for out-of-stock items; clicking displays 'Out of Stock'.

**Actual Result:**
Product is added to the cart successfully, allowing checkout of unfulfillable inventory.

---

### <a id="bug-008"></a>[BUG-008] Cart quantity input accepts negative values and recalculates total negatively

| Attribute | Specification Details |
| :--- | :--- |
| **Defect ID** | `BUG-008` |
| **Module** | Shopping Cart & Cart Actions |
| **Severity** | **Critical** |
| **Priority** | **High (P1)** |
| **Status** | **Open** |
| **Evidence Path** | `evident/bugs/BUG_008_negative_cart_total.png` |
| **Linked Test Case** | `TC-CRT-006` |

**Preconditions:**
Cart contains items.

**Test Data:**
`Quantity: -2`

**Steps to Reproduce:**
1. Add 'Blue Top' ($29.00) to shopping cart and navigate to Cart view.
2. Click quantity input box.
3. Type '-2' and hit Enter.

**Expected Result:**
Input validation replaces the value with '1' or displays an error; minimum boundary is 1.

**Actual Result:**
Cart row total and cart grand total update to a negative currency balance (e.g. -$58.00).

---

### <a id="bug-009"></a>[BUG-009] Removing product row from cart page requires double-clicking the delete 'X' button

| Attribute | Specification Details |
| :--- | :--- |
| **Defect ID** | `BUG-009` |
| **Module** | Shopping Cart & Cart Actions |
| **Severity** | **Low** |
| **Priority** | **Low (P3)** |
| **Status** | **Open** |
| **Evidence Path** | `evident/bugs/BUG_009_double_click_delete.png` |
| **Linked Test Case** | `TC-CRT-007` |

**Preconditions:**
Items present in shopping cart.

**Test Data:**
`Single click on delete icon`

**Steps to Reproduce:**
1. Add a product to cart and go to Cart page.
2. Click the red 'X' button in the product row once.

**Expected Result:**
Product row is deleted immediately on a single click; table row fades out.

**Actual Result:**
Row remains active on first click. Clicking the button a second time removes the item.

---

### <a id="bug-010"></a>[BUG-010] Cart header count badge does not decrement immediately when deleting an item

| Attribute | Specification Details |
| :--- | :--- |
| **Defect ID** | `BUG-010` |
| **Module** | Shopping Cart & Cart Actions |
| **Severity** | **Medium** |
| **Priority** | **Medium (P2)** |
| **Status** | **Open** |
| **Evidence Path** | `evident/bugs/BUG_010_cart_badge_desync.png` |
| **Linked Test Case** | `TC-CRT-008` |

**Preconditions:**
Cart contains 2 items (header badge shows '2').

**Test Data:**
`Cart count = 2 -> delete 1 item`

**Steps to Reproduce:**
1. Add two items to cart.
2. Navigate to Cart page.
3. Click delete button for one product (Row disappears).

**Expected Result:**
Header cart badge count decreases to '1' dynamically via state broadcast.

**Actual Result:**
Header badge count remains '2' until a manual full page refresh is triggered.

---

### <a id="bug-011"></a>[BUG-011] Applying a valid 10% promo code deducts 100% of order value at checkout

| Attribute | Specification Details |
| :--- | :--- |
| **Defect ID** | `BUG-011` |
| **Module** | Checkout, Billing & Payments |
| **Severity** | **Critical** |
| **Priority** | **High (P1)** |
| **Status** | **Open** |
| **Evidence Path** | `evident/bugs/BUG_011_promo_100_percent_free.png` |
| **Linked Test Case** | `TC-CHK-005` |

**Preconditions:**
User at Checkout page with items in cart ($100.00 total).

**Test Data:**
`Promo Code: 'DISCOUNT10'`

**Steps to Reproduce:**
1. Add products to cart and proceed to Checkout page.
2. Enter valid promo code 'DISCOUNT10' (intended for 10% reduction).
3. Click 'Apply' button.

**Expected Result:**
Subtotal is reduced by exactly 10%, reflecting a 90% customer payment balance ($90.00).

**Actual Result:**
Promo code deducts the entire total ($0.00 due balance), allowing orders to be processed for free.

---

### <a id="bug-012"></a>[BUG-012] Checkout confirmation button remains disabled on Firefox browsers

| Attribute | Specification Details |
| :--- | :--- |
| **Defect ID** | `BUG-012` |
| **Module** | Checkout, Billing & Payments |
| **Severity** | **High** |
| **Priority** | **High (P1)** |
| **Status** | **Open** |
| **Evidence Path** | `evident/bugs/BUG_012_firefox_checkout_disabled.png` |
| **Linked Test Case** | `TC-CHK-006` |

**Preconditions:**
Logged-in user on checkout page with items.

**Test Data:**
`Browser: Mozilla Firefox`

**Steps to Reproduce:**
1. Access cart as logged-in user in Firefox browser.
2. Click 'Proceed to Checkout'.
3. Review address details and scroll to the bottom.

**Expected Result:**
'Place Order' button is enabled and clickable.

**Actual Result:**
Button displays disabled cursor style and ignores clicks, completely blocking Firefox users from purchasing.

---

### <a id="bug-013"></a>[BUG-013] Credit card billing page throws 500 error when expiration year is entered in 2-digit format

| Attribute | Specification Details |
| :--- | :--- |
| **Defect ID** | `BUG-013` |
| **Module** | Checkout, Billing & Payments |
| **Severity** | **Critical** |
| **Priority** | **High (P1)** |
| **Status** | **Open** |
| **Evidence Path** | `evident/bugs/BUG_013_year_2digit_crash.png` |
| **Linked Test Case** | `TC-CHK-007` |

**Preconditions:**
User on payment screen entering card details.

**Test Data:**
`Expiration Year: '28'`

**Steps to Reproduce:**
1. Proceed to payment page with items.
2. Enter valid card details.
3. In Expiration Year field, input: 28 (instead of 2028).
4. Click 'Pay and Confirm Order'.

**Expected Result:**
Form intercepts input and prompts user for 4-digit format, or normalizes it to '2028'.

**Actual Result:**
Page crashes with an unhandled server exception: 'DateTimeParseException: Year must be 4 digits'.

---

### <a id="bug-014"></a>[BUG-014] Tax rate on Checkout summary matches a flat 25% instead of standard 10% tax rate

| Attribute | Specification Details |
| :--- | :--- |
| **Defect ID** | `BUG-014` |
| **Module** | Checkout, Billing & Payments |
| **Severity** | **Medium** |
| **Priority** | **Medium (P2)** |
| **Status** | **Open** |
| **Evidence Path** | `evident/bugs/BUG_014_tax_calculation_mismatch.png` |
| **Linked Test Case** | `TC-CHK-009` |

**Preconditions:**
User reviewing checkout totals.

**Test Data:**
`Item Subtotal: $10.00`

**Steps to Reproduce:**
1. Add a $10.00 product to cart and checkout.
2. Look at Tax calculation line in totals summary.

**Expected Result:**
Tax line displays '$1.00' (10% standard rate).

**Actual Result:**
Tax line displays '$2.50' (applying a 25% flat rate without logic explanation).

---

### <a id="bug-015"></a>[BUG-015] Order confirmation email displays unrendered raw HTML tags in mail client

| Attribute | Specification Details |
| :--- | :--- |
| **Defect ID** | `BUG-015` |
| **Module** | Checkout, Billing & Payments |
| **Severity** | **Low** |
| **Priority** | **Low (P3)** |
| **Status** | **Open** |
| **Evidence Path** | `evident/bugs/BUG_015_raw_html_email.png` |
| **Linked Test Case** | `TC-CHK-012` |

**Preconditions:**
Order placed successfully by registered user.

**Test Data:**
`Email notification trigger`

**Steps to Reproduce:**
1. Checkout and purchase items successfully.
2. Open order confirmation email received in inbox.

**Expected Result:**
Email has nicely styled HTML tables, logo, and formatted message elements.

**Actual Result:**
Email displays plaintext containing raw markup, e.g. 'Dear Customer, <br/> Your order <b>#1029</b> was successful.'

---

### <a id="bug-016"></a>[BUG-016] Contact Us attachment file uploader accepts executable files (.exe)

| Attribute | Specification Details |
| :--- | :--- |
| **Defect ID** | `BUG-016` |
| **Module** | General & Contact Us |
| **Severity** | **High** |
| **Priority** | **High (P1)** |
| **Status** | **Open** |
| **Evidence Path** | `evident/bugs/BUG_016_exe_upload_accepted.png` |
| **Linked Test Case** | `TC-GEN-001` |

**Preconditions:**
User on Contact Us page.

**Test Data:**
`File: 'test_payload.exe'`

**Steps to Reproduce:**
1. Go to Contact Us page.
2. Fill mandatory fields.
3. Click 'Choose File' and select an executable '.exe' payload.
4. Click 'Submit'.

**Expected Result:**
Client and server reject file; prompt informs user only .jpg, .png, .pdf files are accepted.

**Actual Result:**
File uploads without restriction; server saves executable file into static assets directory.

---

