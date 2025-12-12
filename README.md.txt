# Grocery Store API Automation Framework

## 🚀 Project Overview
This project is an automated testing framework for the [Simple Grocery Store API](https://github.com/vdespa/introduction-to-postman-course/blob/main/simple-grocery-store-api.md). It covers End-to-End (E2E) workflows including user registration, product catalog, cart management, and order processing.

## 🛠 Tech Stack
* **Tool:** Postman
* **Runner:** Newman (CLI)
* **Language:** JavaScript (Postman)

## 🧪 Scenarios Covered
* **Happy Path:** Register Client -> Browse Products -> Add to Cart -> Checkout.
* **Negative Testing:** Handling 404s (Invalid Products) and 400s (Duplicate Registration).
* **Data Validation:** Schema checks, Status code validation, and Response time SLAs.

## 📂 Project Structure
* `tests/`: Contains the Postman Collection and Environment JSON files.
* `.github/workflows`: CI/CD pipeline configuration.

## ⚙️ How to Run
**Prerequisites:** Node.js and Newman (`npm install -g newman`)

**Run via Command Line:**
```bash
newman run tests/grocery-store-collection.json -e tests/grocery-store-env.json --folder "Happy Path Flow"