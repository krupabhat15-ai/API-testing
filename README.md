# Enterprise e-Commerce API Functional & Boundary Validation Suite

This repository showcases a structured, production-ready Postman Collection engineered to validate functional data persistence, schema routing, and error-handling constraints below the user interface layer. 

The suite simulates a core transactional e-Commerce order pipeline, interacting with a cloud gateway to evaluate how backend databases handle structured data states without a web browser frontend.

## Core Testing Scenarios Executed

* **Scenario 1: Happy Path Product Resource Creation (POST)**
  * **Objective:** Validates that the backend accurately processes complex, nested JSON objects and registers new product records.
  * **Validation Check:** Asserts that the server establishes data persistence, issues a success status code, and allocates a unique, non-null database record tracking ID.

* **Scenario 2: Data State Retrieval & Persistence Verification (GET)**
  * **Objective:** Isolates the database layer to ensure the newly created resource is accurately retrievable via its unique identifier.
  * **Validation Check:** Asserts that endpoint queries return a matching data layout geometry, ensuring zero data corruption during transit.

* **Scenario 3: Schema Structural Boundary Check (POST)**
  * **Objective:** Tests the application's input handling by intentionally passing an invalid flat text string instead of a structured nested JSON data object.
  * **Actual Outcome observed:** The outer web server layer intercepts the structurally malformed payload and throws an immediate **405 Method Not Allowed** status code. This confirms that structural schema mismatches are rejected at the server gateway layer before penetrating the inner database routing engine.


## How to Import and Run This Project

1. Download the `eCommerce_Order_Validation_Suite.postman_collection.json` file from this repository to your laptop.
2. Launch your desktop Postman application.
3. Click the **Import** button located in the top-left navigation panel.
4. Drag and drop the downloaded JSON file into the execution pane.
5. Expand the collection sidebar, review the body payloads, and click **Send** on each request to witness live cloud database transactions.
