# Artemis AI Android Automation Testing Framework

## Introduction
**Artemis** is a robust and scalable foundation for automating **Android application testing** using **Appium** with **Java**.
It leverages Appium (UiAutomator2) for mobile automation, TestNG for test execution, and Gradle for build management.
The framework is designed for maintainability, modularity, and readability by implementing the **Page Object Model (POM)**, and adds an **AI-assisted layer** to make test creation and maintenance faster and more resilient.
Advanced HTML reports are supported via **Allure Reporting**, enabling easy analysis of test results.

<!-- Add a framework overview image here -->
<!-- <img width="646" height="400" alt="overview" src="path/to/overview.png" /> -->

---

## Technologies & Tools Used

| Tool / Library            | Purpose                                         |
| ------------------------- | ----------------------------------------------- |
| Java                      | Programming language                            |
| Appium (UiAutomator2)     | Android mobile automation                       |
| Android SDK / ADB         | Device and emulator management                  |
| TestNG                    | Test execution framework                        |
| Gradle                    | Build automation and dependency management      |
| Allure Reporting          | Advanced HTML test reporting                    |
| AI integration            | AI-assisted test generation and self-healing    |

---

## Prerequisites

Ensure the following tools are installed before running the framework:

* Java JDK 11 or higher
* Gradle (or use the included Gradle wrapper)
* Node.js and Appium 2.x (`npm install -g appium`)
* Appium UiAutomator2 driver (`appium driver install uiautomator2`)
* Android Studio with Android SDK and `ANDROID_HOME` configured
* An Android emulator or a physical device with USB debugging enabled
* IntelliJ IDEA / Eclipse (optional for development)

---

## Project Structure

```bash
artemis-ai-android-automation-testing-framework/
│
├── .gradle/                        # Gradle-related files
├── .idea/                          # IDE configuration files
├── allure-report/                  # Generated Allure HTML reports
├── allure-results/                 # Allure raw results (JSON, attachments)
├── build/                          # Build artifacts
├── gradle/                         # Gradle wrapper files
├── src/
│   ├── main/                       # Reserved for main application code (currently empty)
│   └── test/
│       ├── java/
│       │   ├── pages/              # Page Object classes (one per app screen)
│       │   ├── setup/              # Driver and device setup classes
│       │   ├── testrunner/         # Test runner classes (TestNG)
│       │   ├── ai/                 # AI-assisted helpers (test generation, self-healing)
│       │   └── utils/              # Utility/helper classes
│       └── resources/
│           ├── apps/               # APK files under test
│           ├── screenshots/        # Screenshots captured during tests
│           ├── suites/             # Test suite XML files
│           ├── config.properties   # Configuration (device, app path, Appium URL)
│           └── TestData.json       # Test data
│
├── .gitignore                      # Git ignore rules
├── build.gradle                    # Gradle build file
├── gradlew                         # Gradle wrapper (Linux/Mac)
├── gradlew.bat                     # Gradle wrapper (Windows)
├── README.md                       # Project documentation
└── settings.gradle                 # Gradle settings
```

---

## How to Run This Project

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/artemis-ai-android-automation-testing-framework.git
cd artemis-ai-android-automation-testing-framework
```

### 2. Configure the Environment

Edit `src/test/resources/config.properties`:

```properties
platformName=Android
deviceName=emulator-5554
appPath=src/test/resources/apps/your-app.apk
appiumServerUrl=http://127.0.0.1:4723
```

Never commit real credentials or API keys. Keep secrets in environment variables or an untracked file.

### 3. Start the Appium Server and Device

```bash
appium
```

Start an Android emulator, or connect a physical device and confirm it is visible:

```bash
adb devices
```

### 4. Run the Tests

```bash
./gradlew clean test
```

### 5. Generate Allure Report (Optional)

```bash
./gradlew allureServe
```

> This will start a local server with interactive test reports in your browser.

---

## Test Report

After test execution, Allure raw results are generated at:

```bash
build/allure-results/
```

<!-- Add report screenshots here -->
<!-- <img width="1892" height="975" alt="allure-report" src="path/to/report.png" /> -->

> The report provides detailed insights into test execution, including pass/fail status, screenshots, and logs.

---

## Report Customization

The framework supports **Allure Reporting** with custom metadata such as environment, platform, device, and test author.

**Sample Configuration in TestNG Listener:**

```java
import io.qameta.allure.Allure;

@BeforeMethod
public void beforeTest(Method method) {
    Allure.parameter("Platform", "Android 14");
    Allure.parameter("Device", "Pixel 7 Emulator");
    Allure.parameter("Environment", "QA");
    Allure.parameter("Author", "Your Name");
}
```

---

## Features

* **Android automation** on emulators and real devices
* **Page Object Model (POM)** implementation
* **AI-assisted testing**: test case generation and self-healing locators
* **Explicit and dynamic wait handling** for stable tests
* **Screenshots on failure** attached to the report
* **Allure reporting** with detailed steps and metadata
* **Gradle-based project setup** for easy dependency management
* **Configurable** device, app, and server settings

---

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes
4. Push to the branch and open a pull request

---
