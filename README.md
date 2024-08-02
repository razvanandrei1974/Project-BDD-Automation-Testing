# _**QA-Automation-Project-Parabank-website**_ 🔄

📍We created the automated test plan with Behave for the _"Login"_ menu , _"Register"_ menu abd _Open Account_ menu for the Parabank application.

📍We used the Selenium library to automate the actions of navigation and interaction with the web interface.

## 📌 Installation and configuration:

🖥️ I installed Behave, Selenium library, WebDriver for Python.


## ▶️ Definition of test scenarios:

1. Create _Features_ directory which includes the following files :

  ## $${\color{green}login.features}$$
   
   ▶️ Functionality Menu Login with real and corect data.
   
```ruby
  Feature: Login Feature
  Background:
    Given I am on the login page
  @first
  Scenario: Login with wrong credentials

    When I enter "Razvan1199774499@" in username field
    And I enter "Bnc48757960$" in password field
    And I press the login button
    Then I should see an error message
```





