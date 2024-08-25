.. AutodefenseML-docs documentation master file, created by
   sphinx-quickstart on Sun Aug 25 12:43:26 2024.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

AutodefenseML documentation
================================

Welcome to the ML Security Testing Platform documentation. This guide will help you understand the purpose of the platform, how to get started, and how to effectively use its features.

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   introduction
   getting_started
   platform_navigation
   creating_managing_projects
   running_evaluations
   viewing_results
   troubleshooting_debugging
   security_compliance
   exporting_sharing_results
   limitations_constraints
   future_updates
   support_resources

Introduction
============

Overview of the Platform
------------------------

Welcome to the ML Security Testing Platform, a powerful tool designed to automate security testing and vulnerability assessment for machine learning models. The platform provides an end-to-end solution for evaluating models and datasets, identifying potential security threats, and suggesting defensive strategies to mitigate risks. The goal is to ensure that your machine learning models are robust, secure, and ready for deployment in real-world environments.

Who Should Use This Platform?
-----------------------------

This platform is tailored for machine learning engineers and practitioners who may have limited knowledge of adversarial machine learning or who want to stay up-to-date with the latest attacks and defenses.

Key Features
------------

- Automatic Model Evaluation: Test your models against a variety of adversarial attacks and receive recommendations for defenses.
- Dataset Evaluation: Analyze your datasets for signs of poisoning attacks, ensuring the integrity of your training data.
- Bias Evaluation: Detect and mitigate bias in your datasets, ensuring fairness in model predictions.

Getting Started
===============

This section will guide you through the initial steps of using the ML Security Testing Platform, from understanding user roles and system requirements to logging in and navigating the platform.

User Roles & Permissions
------------------------

At this stage, the platform is primarily designed for machine learning engineers who are responsible for testing and securing machine learning models. There are no specific role-based permissions implemented yet, so all users have equal access to the platform's features.

System Requirements
-------------------

Before using the platform, ensure that your system meets the following minimum requirements:

- Supported Browsers:
  - Google Chrome (latest version)
  - Mozilla Firefox (latest version)
  - Microsoft Edge (latest version)
- Internet Connection:
  - A stable internet connection is necessary for uploading assets (models, datasets) and for interacting with the cloud-based services that power the evaluations.
- Optional:
  - If you're using the platform’s advanced features, such as custom environments or specialized model configurations, ensure you have access to your development environment to create the necessary configuration files (e.g., Python requirements files).

Login and Authentication
-------------------------

To access the platform, you'll need to create an account and log in.

Platform Navigation
===================

Once logged in, you’ll land on the main dashboard. Here's an overview of how to navigate through the platform:

Main Dashboard
--------------

The dashboard provides a centralized overview of your activities on the platform.

Tabs/Sections
-------------

Each tab or section represents one of the evaluation categories.

Creating and Managing Projects
==============================

Starting a New Project
----------------------

### Uploading Models and Datasets

Before running any evaluations, users need to upload their models and datasets.

### Model Wrapper Interface

- **Purpose**: To ensure compatibility with the platform, all models must be wrapped using a specific interface.

### Dataloader Interface

- **Purpose**: The dataloader interface standardizes the way datasets are handled.

Configuring Environment Settings
--------------------------------

- **Python Requirements File**: Users may need to upload a Python requirements file (requirements.txt) to specify any additional libraries or dependencies their model or dataloader requires.

Validation Process
------------------

- **Purpose**: Before running an evaluation, the platform must validate that all uploaded assets are correctly configured and can be executed without errors.

Running Evaluations
===================

The ML Security Testing Platform provides three types of evaluations: Model Evaluation, Dataset Evaluation, and Bias Evaluation. This section will guide you through the steps for each evaluation type, detailing the supported models, datasets, and how to interpret the results.

Model Evaluation
-----------------

Model Evaluation focuses on testing machine learning models against adversarial attacks to assess their robustness and security. The evaluation provides insights into the vulnerabilities of your model and suggests potential defenses.

Supported Model Types and Frameworks
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The platform supports a wide range of machine learning frameworks, making it adaptable to various model types:

- **Frameworks:** TensorFlow, PyTorch, sklearn, Xgboost, and CatBoost are currently supported.
- **Model Types:**
  - Classification models are fully supported.
  - Primarily tested with image and tabular data models.
  - Support for regression models and other data types is planned for future updates.

.. note::
    Ensure that your model conforms to the platform's expected interface. You may need to wrap your model using our provided Python class templates for compatibility.

Steps for Running Model Evaluations
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. **Create a New Project:** In the Model Evaluation section, click on the "New Project" button.
2. **Upload Model and Assets:** Upload your model, any necessary datasets, and supporting files (e.g., data loaders). You can choose from the provided templates if needed.
3. **Configure Evaluation Settings:**
   - Select the attack scenarios you want to evaluate (blackbox or whitebox attacks).
   - Optional: Enable hyperparameter optimization to automatically test various defense configurations.
4. **Validate Configuration:** Before running the evaluation, click "Validate" to ensure that all assets and configurations are correct. The platform will check for issues like incorrect file formats, incompatible configurations, or missing dependencies.
5. **Run Evaluation:** Once validation is successful, click "Run Evaluation." The platform will automatically perform the tests and notify you when the evaluation is complete.

Interpreting Results
~~~~~~~~~~~~~~~~~~~~

After the evaluation completes, you'll receive two types of outputs:

1. **Raw JSON Results:** This file contains detailed information about the adversarial attacks tested on your model, including attack success rates, model vulnerabilities, and performance under different scenarios.
2. **PDF Summary Report:** This report provides an executive summary of the results, including:
   - **Blackbox vs. Whitebox Attacks:** An analysis of how your model performs against attacks with varying knowledge of the internal model.
   - **Adaptive Adversaries:** A section that evaluates how your model stands up to attackers who adapt their strategies based on initial failures.
   - **Recommended Defenses:** Suggestions for preprocessor defenses and their optimal hyperparameters based on the observed vulnerabilities.

Dataset Evaluation
------------------

Dataset Evaluation helps detect potential data poisoning attacks that could compromise the integrity of your training data. This evaluation focuses on identifying harmful manipulations that may have occurred within your dataset.

Steps for Running Dataset Evaluations
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. **Create a New Project:** Navigate to the Dataset Evaluation section and click "New Project."
2. **Upload Dataset:** Provide the dataset you wish to evaluate. Ensure that the dataset is in a supported format (e.g., CSV for tabular data).
3. **Select Evaluation Settings:**
   - Choose the type of poisoning attack detection you want to run. The platform currently uses a generic algorithm for detecting a range of poisoning strategies.
4. **Validate Configuration:** Click "Validate" to ensure that your dataset is correctly formatted and that all required configurations are in place.
5. **Run Evaluation:** Once validation is successful, click "Run Evaluation." The platform will notify you upon completion.

Supported Data Types and Constraints
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- **Supported Data Types:** Tabular datasets are currently supported for dataset evaluation.
- **Constraints:** The platform currently does not support text or image datasets for poisoning detection. These will be added in future updates.

Understanding Poisoning Attack Detection Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The results from the Dataset Evaluation will be provided in the following formats:

1. **Raw JSON Results:** A comprehensive report detailing the detected poisoning patterns, including affected data points and the confidence levels of the detections.
2. **PDF Summary Report:** A user-friendly report that summarizes the poisoning attacks found in the dataset, along with suggestions for cleaning or mitigating the effects of the poisoned data.

Bias Evaluation
---------------

Bias Evaluation aims to detect and mitigate bias present in your dataset, ensuring that your model treats different groups fairly. This evaluation helps identify systemic bias that could lead to unethical or illegal discrimination in model predictions.

Steps for Running Bias Evaluations
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. **Create a New Project:** Go to the Bias Evaluation section and click "New Project."
2. **Upload Dataset:** Upload the dataset you want to evaluate for bias. Currently, the platform supports tabular datasets (e.g., CSV files).
3. **Select Evaluation Settings:**
   - Choose the bias detection method and the types of bias you want to evaluate (e.g., demographic parity, equal opportunity).
   - Optional: Enable bias mitigation strategies, which the platform will automatically apply and evaluate.
4. **Validate Configuration:** Click "Validate" to check the dataset and configurations.
5. **Run Evaluation:** Once validation is successful, click "Run Evaluation." The platform will notify you when the evaluation is finished.

Supported Data Types and Bias Mitigation Methods
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- **Supported Data Types:** Currently, only tabular datasets are supported for bias evaluation.
- **Bias Mitigation Methods:** The platform provides several automated bias mitigation techniques that can be applied to your dataset, including re-weighting, re-sampling, and algorithmic adjustments.

Understanding Bias Detection and Mitigation Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The results from the Bias Evaluation will include:

1. **Raw JSON Results:** Detailed findings about bias in the dataset, including which groups are disproportionately affected and the extent of the bias.
2. **PDF Summary Report:** A high-level overview of the bias evaluation results, including:
   - **Bias Detection:** Identification of biased outcomes in your dataset and how they affect model performance.
   - **Bias Mitigation:** A summary of the mitigation strategies applied and their effectiveness, with recommendations for further improvements.

Troubleshooting and Debugging
=============================

- **Validation and Analysis Errors**: Common issues (dataset format, model parameters, runtime failures, etc.).

Security and Compliance
=======================

- **Data Confidentiality**: How data is stored and managed on GCP.
- **License and Rights Information**: Placeholder for legal and licensing details.

Exporting and Sharing Results
=============================

- **Downloading Results**: Steps to download JSON and PDF files.

Limitations and Constraints
===========================

- **Current Limitations**: Current limitations of model, dataset, and bias evaluations.

Future Updates
==============

- **Upcoming Features**: Targeted adversarial attacks, model theft, and other confidentiality attacks.

Support and Resources
=====================

- **Help and Documentation**: Links to further documentation, FAQs, and support.
- **Contact Information**: How to reach support for technical issues or feedback.
