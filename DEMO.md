# Sonar Demo — Spring PetClinic

This repository is used as a demo project for Sonar Solution Engineering.
It showcases SonarCloud integration on a real-world Java/Spring Boot application.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [SonarCloud Setup](#sonarcloud-setup)
   - [Step 1 — Import the repository](#step-1--import-the-repository)
   - [Step 2 — Disable Automatic Analysis](#step-2--disable-automatic-analysis)
   - [Step 3 — Configure GitHub CI](#step-3--configure-github-ci)
3. [Key Sonar Features to Demo](#key-sonar-features-to-demo)

---

## Project Overview

- **Language:** Java 17
- **Framework:** Spring Boot 4
- **Build tools:** Maven, Gradle
- **CI:** GitHub Actions
- **Code quality:** SonarCloud

---

## SonarCloud Setup

### Step 1 — Import the repository

From your SonarCloud organization dashboard, click **Analyze new project**, select this repository, and let SonarCloud run its first automatic analysis.

> Official docs: [Importing your project](https://docs.sonarsource.com/sonarcloud/getting-started/github/)

---

### Step 2 — Disable Automatic Analysis

Automatic Analysis does not support code coverage reporting. Switching to CI-based analysis allows SonarCloud to pick up the JaCoCo coverage report generated during the Maven build.

1. In your SonarCloud project, go to **Administration** → **Analysis Method**
2. Turn off the **"SonarCloud Automatic Analysis"** toggle

> Official docs: [Choosing an analysis method](https://docs.sonarsource.com/sonarcloud/advanced-setup/ci-based-analysis/overview/)

---

### Step 3 — Configure GitHub CI

1. Generate a token in SonarCloud (**My Account** → **Security**) and add it as a GitHub Actions secret named **`SONAR_TOKEN`** (**Settings** → **Secrets and variables** → **Actions**)
2. In `.github/workflows/demo.yml`, update the `-Dsonar.projectKey` and `-Dsonar.organization` values with those of your SonarCloud project

The workflow triggers on pushes to the `demo` branch and on pull requests.

> Official docs: [Generating and using tokens](https://docs.sonarsource.com/sonarcloud/advanced-setup/user-accounts/managing-tokens/)
> Official docs: [GitHub Actions integration](https://docs.sonarsource.com/sonarcloud/advanced-setup/ci-based-analysis/github-actions-for-sonarcloud/)

---

