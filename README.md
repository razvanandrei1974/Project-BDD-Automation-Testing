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

## 2. Create _Pages_ directory which includes the following files :


## 2.1. $${\color{darkorange}login-page}$$
``ruby
from selenium.webdriver.common.by import By

from browser import Browser


class LoginPage(Browser):
    USERNAME_FIELD_SELECTOR = (By.XPATH, '/html/body/div[1]/div[3]/div[1]/div/form/div[1]/input')
    PASSWORD_FIELD_SELECTOR = (By.XPATH, '/html/body/div[1]/div[3]/div[1]/div/form/div[2]/input')
    LOGIN_BUTTON_SELECTOR = (By.XPATH, '/html/body/div[1]/div[3]/div[1]/div/form/div[3]/input')
    MESSAGE_ERROR_LABEL = (By.XPATH, '//*[@id="rightPanel"]/p')

    def navigate_to_login_page(self):
        self.driver.get("https://parabank.parasoft.com/parabank/index.htm?ConnType=JDBC")

    def enter_username(self, username):
        self.driver.find_element(*self.USERNAME_FIELD_SELECTOR).send_keys(username)

    def enter_password(self, password):
        self.driver.find_element(*self.PASSWORD_FIELD_SELECTOR).send_keys(password)

    def click_login_button(self):
        self.driver.find_element(*self.LOGIN_BUTTON_SELECTOR).click()

    def get_error_message(self):
        return self.driver.find_element(*self.MESSAGE_ERROR_LABEL).text
```

## 2.2. $${\color{darkorange}register-page}$$

```ruby
from selenium.webdriver.common.by import By

from browser import Browser


class RegisterPage(Browser):
    # LOGOUT_BUTTON_SELECTOR = (By.XPATH, '/html/body/div[1]/div[3]/div[1]/ul/li[8]/a')
    REGISTER_BUTTON_SELECTOR = (By.CSS_SELECTOR, '#loginPanel > p:nth-child(3) > a')
    FIRSTNAME_FIELD_SELECTOR = (By.XPATH, '/html/body/div[1]/div[3]/div[2]/form/table/tbody/tr[1]/td[2]/input')
    LASTNAME_FIELD_SELECTOR = (By.XPATH, '/html/body/div[1]/div[3]/div[2]/form/table/tbody/tr[2]/td[2]/input')
    ADRESS_FIELD_SELECTOR = (By.XPATH, '/html/body/div[1]/div[3]/div[2]/form/table/tbody/tr[3]/td[2]/input')
    CITY_FIELD_SELECTOR = (By.XPATH, '/html/body/div[1]/div[3]/div[2]/form/table/tbody/tr[4]/td[2]/input')
    STATE_FIELD_SELECTOR = (By.XPATH, '/html/body/div[1]/div[3]/div[2]/form/table/tbody/tr[5]/td[2]/input')
    ZIPCODE_FIELD_SELECTOR = (By.XPATH, '/html/body/div[1]/div[3]/div[2]/form/table/tbody/tr[6]/td[2]/input')
    PHONE_FIELD_SELECTOR = (By.XPATH, '/html/body/div[1]/div[3]/div[2]/form/table/tbody/tr[7]/td[2]/input')
    SSN_FIELD_SELECTOR = (By.XPATH, '/html/body/div[1]/div[3]/div[2]/form/table/tbody/tr[8]/td[2]/input')
    USER_FIELD_SELECTOR = (By.XPATH, '//*[@id="customer.username"]')
    PASSW_FIELD_SELECTOR = (By.XPATH, '//*[@id="customer.password"]')
    CONFIRM_FIELD_SELECTOR = (By.XPATH, '//*[@id="repeatedPassword"]')
    SUBMIT_BUTTON_SELECTOR = (By.XPATH, '//*[@id="customerForm"]/table/tbody/tr[13]/td[2]/input')
    MESSAGE_ERROR_LABEL = (By.XPATH, '//*[@id="repeatedPassword.errors"]')

    def navigate_to_register_page(self):
        self.driver.get("https://parabank.parasoft.com/parabank/index.htm?ConnType=JDBC")

    def click_register_button(self):
        self.driver.find_element(*self.REGISTER_BUTTON_SELECTOR).click()

    def enter_firstname(self, Razvan):
        self.driver.find_element(*self.FIRSTNAME_FIELD_SELECTOR).send_keys(Razvan)

    def enter_lastname(self, Ungar):
        self.driver.find_element(*self.LASTNAME_FIELD_SELECTOR).send_keys(Ungar)

    def enter_adress(self, Ciocarliei):
        self.driver.find_element(*self.ADRESS_FIELD_SELECTOR).send_keys(Ciocarliei)

    def enter_city(self, Resita):
        self.driver.find_element(*self.CITY_FIELD_SELECTOR).send_keys(Resita)

    def enter_state(self, CarasSeverin):
        self.driver.find_element(*self.STATE_FIELD_SELECTOR).send_keys(CarasSeverin)

    def enter_zipcode(self, Z320038):
        self.driver.find_element(*self.ZIPCODE_FIELD_SELECTOR).send_keys(Z320038)

    def enter_phone(self, P0726165557):
        self.driver.find_element(*self.PHONE_FIELD_SELECTOR).send_keys(P0726165557)

    def enter_ssn(self, SSN1740827354807):
        self.driver.find_element(*self.SSN_FIELD_SELECTOR).send_keys(SSN1740827354807)

    def enter_user(self, Razvan11997744):
        self.driver.find_element(*self.USER_FIELD_SELECTOR).send_keys(Razvan11997744)

    def enter_passw(self, Bnc48757960):
        self.driver.find_element(*self.PASSW_FIELD_SELECTOR).send_keys(Bnc48757960)

    def enter_confirm_field(self, Bnc487579601):
        self.driver.find_element(*self.CONFIRM_FIELD_SELECTOR).send_keys(Bnc487579601)

    def click_submit_button(self):
        self.driver.find_element(*self.SUBMIT_BUTTON_SELECTOR).click()

    def get_message(self):
        return self.driver.find_element(*self.MESSAGE_ERROR_LABEL).text
```

## 2.3. $${\color{darkorange}openaccount-page}$$

``` ruby
from behave import given, when, then
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import Select


@given('I am on the open account page')
def step_given_on_open_account_page(context):
    context.browser = webdriver.Chrome()
    context.browser.get('https://parabank.parasoft.com/parabank/openaccount.htm')


@when('I fill in the account details')
def step_when_fill_in_account_details(context):
    # Select account type
    account_type_dropdown = Select(context.browser.find_element(By.ID, 'type'))
    account_type_dropdown.select_by_visible_text('SAVINGS')

    # Select from account
    from_account_dropdown = Select(context.browser.find_element(By.ID, 'fromAccountId'))
    from_account_dropdown.select_by_index(0)  # Select the first account in the list


@when('I submit the form')
def step_when_submit_form(context):
    submit_button = context.browser.find_element(By.XPATH, '//input[@value="Open New Account"]')
    submit_button.click()


@then('I should see a confirmation message')
def step_then_see_confirmation_message(context):
    confirmation_message = context.browser.find_element(By.XPATH, '//h1[text()="Account Opened!"]')
    assert confirmation_message.is_displayed()

```

## 3. Create _Steps_ directory which includes the following files :















