# API Testing Suite: Automation Exercise

This directory contains a complete **Postman API Testing Suite** designed to verify the backend API endpoints of **[Automation Exercise](https://automationexercise.com/api_list)**.

It includes a Postman collection containing **12 distinct request scenarios** testing functional logic, boundary values, error responses (unsupported methods, missing parameters), user lifecycle (create, verify, delete), and schema structures.

---

## 📂 Deliverables
1.  **[AutomationExercise_API.postman_collection.json](AutomationExercise_API.postman_collection.json):** The Postman Collection file containing requests, request body parameters, and JS assertions.
2.  **[AutomationExercise_Env.postman_environment.json](AutomationExercise_Env.postman_environment.json):** The Postman Environment variables file including base configurations (`base_url`, test credentials).

---

## 🛠️ Endpoints Covered & Scenarios Tested

### 1. Products API
*   **Get All Products List (`GET /api/productsList`):** Checks successful response, products array schema validation, and verifying that product object details (`id`, `name`, `price`, `brand`, `category`) are present.
*   **Post to All Products (`POST /api/productsList`):** Verifies error response for unsupported HTTP method.
*   **Post to Search Product (`POST /api/searchProduct`):** Verifies search functionality using `search_product` form-data parameter.
*   **Search Product Without Parameter (`POST /api/searchProduct`):** Verifies system behavior and custom validation error message when parameter is missing.

### 2. Brands API
*   **Get All Brands List (`GET /api/brandsList`):** Asserts list extraction and verifies brand list array length.
*   **Put to All Brands (`PUT /api/brandsList`):** Verifies error handling for unsupported HTTP method.

### 3. Authentication & User Lifecycle API
*   **Verify Login (Valid) (`POST /api/verifyLogin`):** Tests authentication with valid registered credentials.
*   **Verify Login (Invalid) (`POST /api/verifyLogin`):** Tests authentication error responses for unregistered accounts.
*   **Verify Login (Missing Parameter) (`POST /api/verifyLogin`):** Validates error output when the `email` key is not provided in form-data.
*   **Delete verifyLogin Session (`DELETE /api/verifyLogin`):** Checks handling of unsupported HTTP method.
*   **Get User Detail by Email (`GET /api/getUserDetailByEmail`):** Checks query parameter extraction and validates schema of returned `user` object.
*   **Create/Register Account (`POST /api/createAccount`):** Verifies registration of new user accounts using multi-part form parameters.
*   **Delete User Account (`DELETE /api/deleteAccount`):** Asserts successful deletion of account, cleaning up database state.

---

## 🧪 Testing Assertion Strategy
Due to the unique architectural design of `automationexercise.com`, the API returns HTTP status code `200 OK` even for error states, but embeds a custom `responseCode` and `message` inside the JSON response payload (e.g., `responseCode: 405`, `message: "This request method is not supported."`).

The assertion scripts in this collection cover:
1.  **HTTP Web Server Assertion:**
    ```javascript
    pm.test("HTTP Status code is 200", function () {
        pm.response.to.have.status(200);
    });
    ```
2.  **Application Logic Assertion:**
    ```javascript
    pm.test("Application responseCode is 405", function () {
        var jsonData = pm.response.json();
        pm.expect(jsonData.responseCode).to.eql(405);
    });
    ```
3.  **Schema / Property Validation:**
    ```javascript
    pm.test("User detail schema verification", function () {
        var jsonData = pm.response.json();
        pm.expect(jsonData.user).to.have.all.keys('id', 'name', 'email', 'first_name', 'last_name', 'address1', 'city', 'state', 'zipcode', 'country');
    });
    ```

---

## 🚀 How to Import and Run in Postman

### Step 1: Import Files into Postman
1.  Open **Postman Desktop app** or go to the Web interface.
2.  Click **Import** in the top left.
3.  Choose **Files** and upload:
    *   `AutomationExercise_API.postman_collection.json`
    *   `AutomationExercise_Env.postman_environment.json`

### Step 2: Select Environment
1.  In the top right corner of Postman, expand the Environment dropdown menu.
2.  Select **Automation Exercise - Production Env**.

### Step 3: Run the Collection
1.  Navigate to your Collections sidebar and select **Automation Exercise API Testing Suite**.
2.  Click on **Run** button (Collection Runner).
3.  Keep default settings and click **Run Automation Exercise API...**
4.  Verify that all test cases execute and return green checkmarks (Passing).

---

## 🖥️ Command Line Execution (Newman)
To run this suite via the CLI (ideal for CI/CD integration):
```bash
# Install newman globally
npm install -g newman

# Execute the test collection with the environment
newman run AutomationExercise_API.postman_collection.json -e AutomationExercise_Env.postman_environment.json
```
