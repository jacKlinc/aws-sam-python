# AWS SAM Python Hello World

This project is a sample AWS Lambda application written in Python, using the AWS Serverless Application Model (AWS SAM). The application demonstrates a simple API that returns a "Hello World" message. It includes unit tests, integration tests, and a CI pipeline configured with GitHub Actions.


## Getting Started

To get started with this project, you'll need to have Python and AWS SAM CLI installed. You can clone this repository and deploy the application locally or on AWS.

### Clone the Repository

```bash
git clone https://github.com/jacKlinc/aws-sam-python.git
cd aws-sam-python
```

### Install Dependencies

You can install the dependencies using `pip`:

```bash
pip install -r hello_world/requirements.txt
```

## Prerequisites

- **Python 3.8 or higher**
- **AWS SAM CLI**: Install the [AWS SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/install-sam-cli.html) to build, test, and deploy the application.
- **AWS Account**: An AWS account is required to deploy the application to AWS.
- **AWS CLI**: Configure your AWS CLI with appropriate credentials for deploying the application.


## Deployment

### Local Deployment

You can build and deploy the application locally using the AWS SAM CLI:

```bash
sam build
sam local invoke "HelloWorldFunction" -e events/event.json
```

### Deploy to AWS

To deploy the application to your AWS account, use the following command:

```bash
sam deploy --guided
```

This will prompt you to specify certain parameters like the stack name, region, and whether you want to save these settings for future deployments.

## Running Tests

The project includes unit and integration tests. Tests can be run using `pytest`.

### Unit Tests

Run unit tests with the following command:

```bash
python -m pytest tests/unit
```

### Integration Tests

Integration tests interact with deployed AWS resources. Ensure the stack is deployed before running these tests:

```bash
python -m pytest tests/integration
```

## CI Pipeline

The project uses GitHub Actions to run the CI pipeline. The pipeline is triggered on push and pull request events. It performs the following actions:

- Runs unit tests on push.
- Runs integration tests on pull requests targeting the `main` branch.
- Deploys the application to AWS when a pull request is merged into the `main` branch.

### CI Pipeline Configuration

The CI pipeline is defined in `.github/workflows/ci.yml`. The pipeline includes the following jobs:

- **Unit Tests**: Runs on every push event.
- **Integration Tests**: Runs on pull request merges to the `main` branch.
- **Deployment**: Deploys the application to AWS when a PR is merged into `main`.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

---

This `README.md` provides an overview of the project, instructions for getting started, and details about the CI pipeline and testing setup. Make sure to update any specific details, like the AWS region or stack name, as needed for your project.