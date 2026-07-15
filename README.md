<div align="center">

# 🧪 Web Testing Project

A manual and automated testing project for the official website of the town of Bzenec, created for the **AP4ST – Software Testing** course at Tomas Bata University in Zlín.

The repository demonstrates test analysis, test-suite organization, reusable test data, and browser-based automation using Robot Framework and SeleniumLibrary.

![Robot Framework](https://img.shields.io/badge/Robot_Framework-automation-00C0B5?logo=robotframework&logoColor=white)
![Selenium](https://img.shields.io/badge/Selenium-web_testing-43B02A?logo=selenium&logoColor=white)
![Python](https://img.shields.io/badge/Python-required-3776AB?logo=python&logoColor=white)
![Testing](https://img.shields.io/badge/testing-manual_%26_automated-blue)
![License](https://img.shields.io/badge/license-not_specified-lightgrey)

</div>

---

## About the project

This project tests the public website [www.bzenec.cz](https://www.bzenec.cz/) through a combination of:

- manual test suites and test cases,
- automated browser tests,
- reusable keywords and locators,
- structured test hierarchy,
- generated execution reports,
- detailed test documentation.

The goal is to demonstrate different software-testing strategies while keeping test cases organized, reusable, and easy to execute.

---

## Project highlights

- Manual and automated web testing
- Browser automation with Robot Framework and SeleniumLibrary
- Test cases grouped into test suites
- Reusable locators, variables, and keywords
- Object Repository design pattern
- Tagged tests for selective execution
- Positive and alternative test scenarios
- HTML reports and execution logs
- Detailed test specification document

---

## Technology stack

| Area | Technology |
|---|---|
| Test automation | Robot Framework |
| Browser automation | SeleniumLibrary |
| Runtime | Python |
| Test target | Bzenec municipal website |
| Manual documentation | Microsoft Word and text files |
| Test results | Robot Framework HTML/XML output |
| Execution helper | Windows batch script |

---

## Repository structure

```text
WebTesting/
├── Automated/
│   ├── objectRepository/
│   │   ├── Browsers.robot
│   │   ├── Buttons.robot
│   │   ├── Headings.robot
│   │   ├── Images.robot
│   │   ├── Inputs.robot
│   │   ├── Keywords.robot
│   │   ├── Location.robot
│   │   ├── Logo.robot
│   │   ├── Notifikace.robot
│   │   ├── Path.robot
│   │   ├── URLs.robot
│   │   ├── Values.robot
│   │   └── Video.robot
│   ├── results/
│   ├── TC001.robot
│   ├── TC002.robot
│   ├── ...
│   ├── TC041.robot
│   └── run_tests.bat
├── Manual/
│   ├── TS100 - Front End/
│   ├── Hierarchie.txt
│   └── TS100 - Fornt End.txt
├── Specifikace_testu.docx
└── README.md
```

---

## Testing approach

### Manual testing

The `Manual` directory contains the test hierarchy, test-suite definitions, and manually documented test cases.

Manual testing is useful for:

- validating visual behavior,
- checking content and usability,
- exploring unexpected user interactions,
- documenting expected and actual results,
- covering cases that are difficult to automate.

### Automated testing

The `Automated` directory contains Robot Framework test cases. The tests use SeleniumLibrary to open the website, locate page elements, validate their visibility or content, and close the browser after execution.

A simplified example:

```robot
*** Settings ***
Library    SeleniumLibrary
Resource   objectRepository/URLs.robot
Resource   objectRepository/Headings.robot
Resource   objectRepository/Keywords.robot

*** Test Cases ***
Verify Main Heading
    [Tags]    FrontEnd
    Open And Verify URL    ${URL_Bzenec_HomePage}
    Page Should Contain Element    ${Heading_HomePage_MainTitle_XPath}
    Element Should Be Visible      ${Heading_HomePage_MainTitle_XPath}
    Close Browser
```

---

## Getting started

### Prerequisites

Install:

- [Python 3](https://www.python.org/downloads/)
- Google Chrome or another supported browser
- Git

### 1. Clone the repository

```bash
git clone https://github.com/apolkova/WebTesting.git
cd WebTesting
```

### 2. Create a virtual environment

#### Windows

```bash
python -m venv .venv
.venv\Scripts\activate
```

#### macOS or Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install the testing dependencies

```bash
pip install robotframework robotframework-seleniumlibrary selenium
```

### 4. Run one test case

```bash
robot Automated/TC001.robot
```

### 5. Run all automated tests

```bash
robot Automated
```

On Windows, the included batch file can also be used:

```bat
cd Automated
run_tests.bat
```

> Review `run_tests.bat` before execution because it may contain project-specific paths or selected test-case commands.

---

## Running selected tests

Robot Framework tags make it possible to run only a selected group of tests.

For example:

```bash
robot --include FrontEnd Automated
```

Run a particular test suite:

```bash
robot Automated/TC005.robot
```

Choose a custom results directory:

```bash
robot --outputdir Automated/results Automated
```

---

## Test results

Robot Framework normally generates:

```text
output.xml
log.html
report.html
```

Open `report.html` for the execution summary and `log.html` for detailed keyword-level results.

Recommended command:

```bash
robot --outputdir Automated/results Automated
```

After execution, open:

```text
Automated/results/report.html
Automated/results/log.html
```

---

## Object Repository

Reusable test resources are stored in `Automated/objectRepository`.

This separates test logic from page-specific data:

- `URLs.robot` — tested page addresses
- `Browsers.robot` — browser configuration
- `Headings.robot` — heading locators and expected text
- `Buttons.robot` — button locators
- `Inputs.robot` — input-field locators
- `Images.robot` and `Logo.robot` — image locators
- `Values.robot` — expected values and test data
- `Keywords.robot` — reusable testing actions

This structure reduces duplication and makes locator maintenance easier.

---

## Test documentation

The repository includes `Specifikace_testu.docx`, which provides detailed project and testing documentation.

The documentation complements the executable tests by describing areas such as:

- test scope,
- test hierarchy,
- test sets,
- individual test cases,
- expected behavior,
- manual and automated coverage.

---

## Possible improvements

- Add a `requirements.txt` file
- Add cross-platform execution scripts
- Remove generated results from version control where appropriate
- Add screenshots and test-report examples
- Add GitHub Actions for automatic test execution
- Add browser selection through command-line variables
- Improve naming consistency in manual test files
- Add setup and teardown keywords
- Add data-driven and parameterized tests
- Add a license

---

## Author

Developed by [apolkova](https://github.com/apolkova) for the **AP4ST – Software Testing** course at Tomas Bata University in Zlín.
