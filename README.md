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

  ## $${\color{green}login1.features}$$
   
   ▶️ Functionality Menu Login with unreal data.
   
```ruby
  Feature: Login Feature
  Background:
    Given I am on the login page
  @first
  Scenario: Login with wrong credentials

    When I enter "user_name" in username field
    And I enter "password" in password field
    And I press the login button
    Then I should see an error message
```

 ## $${\color{green}register.features}$$

 ```ruby
Feature: Register Feature

  Background:
    Given I am on the register page

  @second
  Scenario: Register with corect and real credentials.

    # When I press the logout button
    When I press the register button
    And I enter "Razvan" in FirstName field
    And I enter "Ungar" in LastName field
    And I enter "Ciocarliei" in Adress field
    And I enter "Resita" in City field
    And I enter "CarasSeverin" in State field
    And I enter "Z320038" in Zip Code field
    And I enter "P0726165557" in Phone field
    And I enter "SSN1740827354807" in SSN field
    And I enter "Razvan11997744" in User field
    And I enter "Bnc48757960" in Passw field
    And I enter "Bnc487579601" in Confirm field
    And I press the submit button
    Then I should see an error register message
```
## $${\color{green}open account.features}$$

```ruby
Feature: Open account

#  Background:
#  As a user
#  I want to open a new account
#  So that I can use the banking services
  @three
  Scenario: Successfully open a new account
    Given I am on the open account page
    When I fill in the account details
    And I submit the form
    Then I should see a confirmation message
```

2. Create _Pages_ directory which includes the following files :


## $${\color{darkorange}login page}$$










