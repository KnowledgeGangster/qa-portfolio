# Pages (Page Object Model)

This folder contains Page Object classes used in the Selenium automation framework.

## Purpose
The `pages/` directory implements the Page Object Model (POM) design pattern to:
- Improve test maintainability
- Reduce code duplication
- Separate test logic from UI structure
- Make tests more readable and scalable

## What This Folder Contains
Each page class represents a page or component of the application:

- LoginPage.py
- HomePage.py
- CheckoutPage.py
- ProductPage.py

## Example Structure
Each page class typically includes:

- Locators (UI elements)
- Actions (click, input, navigation)
- Page-specific methods

## Example (Conceptual)
- login(username, password)
- click_login_button()
- get_error_message()

## Benefits of POM
- Easier test maintenance
- Reusable components
- Cleaner test scripts
- Better separation of concerns

## Skills Demonstrated
- Page Object Model Design
- UI Automation Architecture
- Selenium WebDriver Structuring
- Scalable Framework Design
