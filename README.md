# Software Testing – Survey Web Application

Black-box testing of a PHP web application for creating and filling out surveys, done for the **Software Testing** course (2024/25).

Test plan and report (in Serbian): [Test_Plan_and_Report.pdf](Test_Plan_and_Report.pdf)

Selenium IDE project: [selenium-ide-tests.side](selenium-ide-tests.side)

## Scope

The tested features are:

- **Registration** – validation of the personal ID number (JMBG), name, username, password, date and place of birth, phone number and email
- **Login** – valid and invalid credentials, accounts not approved or blocked by the administrator
- **Password change**
- **Survey creation** – title, start/end dates, question types, question bank, mandatory flag, number of pages
- **Survey completion** – respondent data, answer formats, saving and resuming
- **Administrator rights** – approving registrations, blocking authors, updating and deleting users

## Approach

1. **Equivalence partitioning** – 122 valid and invalid equivalence classes were defined for all input fields and features.
2. **Test plan** – 76 test cases, each with a description, test data, steps, preconditions/postconditions and the equivalence classes it covers.
3. **Execution** – the tests were run in three ways:
   - manually (33)
   - with **Selenium WebDriver** (24)
   - with other automated runs (19)
4. **Test report** – the execution status of each test case, plus a list of the defects found.

## Results

| Total test cases | Passed | Failed |
|:---:|:---:|:---:|
| 76 | 59 | 17 |

**17 defects** were found and documented. Examples:

- Valid phone number formats (e.g. `064xxxxxxx`, `064/xxx-xxx`) are rejected.
- Users can register with a future date of birth or a place of birth that doesn't exist.
- Surveys can be created with an end date in the past or a start date after the end date.
- An invalid year (e.g. `202525`) is accepted and later shown as `0000-00-00`.
- Inserting a question from the question bank reports success even when no question is selected.
- A partially completed survey can't be saved and resumed later, and the "block author" feature is missing.

## Selenium IDE tests

The `.side` project contains 22 automated tests that cover registration validation (phone number, email, JMBG, place of birth), login, password change, profile update, survey creation and survey completion.

To run them:

1. Install the [Selenium IDE](https://www.selenium.dev/selenium-ide/) browser extension.
2. Open `selenium-ide-tests.side`.
3. Start the tested application locally (base URL: `http://localhost/Projekat4/projekat4/ankete2/`).

## Technologies

Selenium IDE · Selenium WebDriver · Black-box testing · Equivalence partitioning
