> [!NOTE]
  > This repository is pinned to specific versions and is intentionally not updated. It serves as a reference for deploying this particular stack on Clever
   Cloud. For a more recent example, check the [examples catalog](https://github.com/CleverCloud/examples-and-demos).

# Python 3 Flask Example on Clever Cloud
[![Clever Cloud - PaaS](https://img.shields.io/badge/Clever%20Cloud-PaaS-orange)](https://clever-cloud.com)

## Overview
This repository provides a complete guide for deploying a Python 3 [Flask](https://flask.palletsprojects.com/) application on [Clever Cloud](https://clever-cloud.com), a European PaaS provider.

[Flask](https://flask.palletsprojects.com/) is a lightweight WSGI web application framework for Python. It's designed to make getting started quick and easy, with the ability to scale up to complex applications. This example demonstrates a minimal Flask application that can be deployed on Clever Cloud with minimal configuration.

## Prerequisites
- A [Clever Cloud](https://www.clever-cloud.com/) account
- [Clever Tools CLI](https://github.com/CleverCloud/clever-tools) installed and configured
- Basic familiarity with command line operations
- Basic understanding of [Python](https://www.python.org/) and [Flask](https://flask.palletsprojects.com/)
- A domain name (optional, but recommended for production use)

## Project Structure

```
├── README.md           # This documentation
├── requirements.txt    # Python dependencies
└── testapp.py         # Main Flask application
```

## Deployment Guide

### Before You Begin
Before starting the deployment process, you'll need to decide on:
- Application Name: Choose a unique name for your Flask application (e.g., my-flask-app)
- Domain Name: Optionally, choose a domain name for your application

You'll use these values throughout the deployment process. In the commands below, replace:
- `<APP_NAME>` with your chosen application name
- `<YOUR_DOMAIN_NAME>` with your domain name (if applicable)

### Using Clever Tools CLI
Follow these steps to deploy your Flask application on Clever Cloud using the command line:

```bash
# Step 1: Create a Python application
clever create --type python <APP_NAME>

# Step 2: Add your domain (optional but recommended)
clever domain add <YOUR_DOMAIN_NAME>

# Step 3: Configure environment variables
clever env set CC_PYTHON_MODULE "testapp:app"
clever env set CC_PYTHON_VERSION "3"

# Step 4: Push your code to Clever Cloud
clever deploy
```

## Opening your application in a browser

Once deployed, you can access your application at `https://<YOUR_DOMAIN_NAME>`.

![Screenshot](/github-assets/screenshot.png)


### Environment Variables
The following environment variables are used to configure your Python application on Clever Cloud:

| Variable | Description | Example Value |
|----------|-------------|---------------|
| `CC_PYTHON_MODULE` | The Python module containing your WSGI application | `testapp:app` |
| `CC_PYTHON_VERSION` | The Python version to use | `3` |

## Running Locally
To run this application locally for testing:

```bash
# Install dependencies
pip install -r requirements.txt

# Run the Flask application
flask --app testapp run --debug
```

Your application will be available at http://127.0.0.1:5000/

## Customizing Your Application

This example provides a minimal Flask application. To expand it:

1. Add routes in `testapp.py` ([Flask Routing Documentation](https://flask.palletsprojects.com/en/3.0.x/quickstart/#routing))
2. Add templates in a `templates` directory ([Flask Templates Documentation](https://flask.palletsprojects.com/en/3.0.x/tutorial/templates/))
3. Add static files in a `static` directory ([Flask Static Files Documentation](https://flask.palletsprojects.com/en/3.0.x/tutorial/static/))
4. Update `requirements.txt` with additional dependencies

Example of adding a new route:

```python
@app.route('/about')
def about():
    return 'About page'
```

## Troubleshooting
If you encounter issues:

1. Check the application logs: `clever logs`
2. Verify all environment variables are correctly set: `clever env`
3. Ensure your application is running: `clever status`

## Contributing
Contributions to improve this deployment example are welcome! Please feel free to submit pull requests or open issues for any enhancements or bug fixes.

## License
This example is provided under the terms of the MIT license.

## Resources
- [Flask Documentation](https://flask.palletsprojects.com/)
- [Flask GitHub Repository](https://github.com/pallets/flask)
- [Clever Cloud Documentation for Python](https://www.clever-cloud.com/doc/deploy/application/python/python/)
- [Clever Cloud Console](https://console.clever-cloud.com/)
