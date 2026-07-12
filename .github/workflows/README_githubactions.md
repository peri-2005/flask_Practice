# Python CI/CD Workflow with GitHub Actions

This repository uses GitHub Actions to automate testing, building, and deploying the application.

## Workflow Triggers

1. **Staging Pipeline:** Triggered automatically on any push to the `staging` branch. Runs tests, builds the package, and deploys to the staging environment.
2. **Production Pipeline:** Triggered automatically when a new release is **published** on GitHub. Runs tests, builds the package, and deploys to the production environment.
3. **Pull Requests / Commits to Main:** Runs testing and validation steps to ensure code quality.

## How to Configure Environment Secrets

To make deployments work safely, you must configure the following GitHub Secrets:

1. Navigate to your GitHub repository.
2. Click on **Settings** -> **Secrets and variables** -> **Actions**.
3. Click the **New repository secret** button.
4. Add the following secrets:
   * `STAGING_API_TOKEN`: The API key or deployment token for your staging server.
   * `PROD_API_TOKEN`: The API key or deployment token for your production infrastructure.

## Workflow Structure

* **Test Job:** Installs dependencies (`pip`) and executes the test suite using `pytest`.
* **Build Job:** Bundles the application using Python `build` and saves it as a workflow artifact.
* **Deploy Staging:** Triggered only on the `staging` branch. Uses `STAGING_API_TOKEN`.
* **Deploy Production:** Triggered only during a GitHub Release event. Uses `PROD_API_TOKEN`.
