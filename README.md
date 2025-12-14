# Grocery Store API Automation Framework

## 🚀 Project Overview
This project is a robust automated testing framework for the [Simple Grocery Store API](https://github.com/vdespa/introduction-to-postman-course/blob/main/simple-grocery-store-api.md). 
It goes beyond basic happy-path testing to include negative scenarios, data integrity checks, and dynamic inventory validation.

## 🛠 Tech Stack
* **Tool:** Postman
* **Runner:** Newman (CLI)
* **Language:** JavaScript (Postman Sandbox)
* **CI/CD:** GitHub Actions (Automated runs on push)

## 🧪 Scenarios Covered

### 1. Happy Path (End-to-End)
* **Registration:** Registers a new client using dynamic email generation (`user_{{$randomInt}}`) to ensure uniqueness every run.
* **Product Discovery:** Browses categories and selects available products.
* **Cart Management:** Adds items, modifies quantities, and verifies cart totals.
* **Checkout:** successfully places an order and returns a valid Order ID.

### 2. Data Validation & Integrity (Advanced)
* **Schema Validation:** Verifies the JSON structure against a strict contract (ensuring keys like `id`, `name`, `price` exist and haven't changed).
* **Type Safety:** Asserts that critical fields have the correct data types (e.g.`inStock` is a Boolean).
* **Business Logic Checks:**
    * **Filtering Logic:** Verifies that query parameters (e.g., `?category=coffee`) return *only* the requested category using array loops.

### 3. Negative Testing & Error Handling
* **Inventory Protection:** dynamically finds "Out of Stock" items, attempts to add them to the cart, and verifies the API correctly blocks the action (`400 Bad Request`).
* **Auth Security:** Verifies that sensitive actions (like Deleting an Order) return `401 Unauthorized` when the Bearer Token is missing or invalid.
* **Invalid Operations:** Tests system behavior when adding invalid Product IDs or modifying deleted carts.

## ⚙️ How to Run
**Prerequisites:** Node.js and Newman (`npm install -g newman`)

**Run the Full Suite:**
```bash
newman run tests/grocery-store-collection.json -e tests/grocery-store-env.json -folder "HappyPathFlow"
newman run tests/grocery-store-collection.json -e tests/grocery-store-env.json -folder "Negative Test Flow" 
