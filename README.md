# Picture Microservice for Django Web Application

This repository contains the microservice responsible for managing picture-related operations within a Django web application. It is part of the [Back-end Development Capstone](https://github.com/berketonoz/Back-end-Development-Capstone) project. This microservice includes APIs for performing CRUD operations on picture data, user authentication, and other related functionalities.

## Table of Contents

- [Features](#features)
- [Architecture](#architecture)
- [Getting Started](#getting-started)
- [Installation](#installation)
- [Deployment](#deployment)
- [Usage](#usage)
- [Running Tests](#running-tests)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Features

- User authentication and authorization
- CRUD operations for pictures
- RESTful APIs with Django Rest Framework
- Search functionality for pictures
- Album management
- Admin interface for managing pictures and users

## Architecture

This microservice is a part of a larger Django web application. It focuses on handling all operations related to pictures, including:

- Creating, reading, updating, and deleting picture records
- User authentication and authorization for accessing picture data
- Managing albums and picture metadata

## Getting Started

These instructions will help you set up the microservice on your local machine for development and testing purposes.

### Prerequisites

- Python 3.x
- Django 3.x or higher
- pip (Python package installer)
- MongoDB

### Installation

1. Clone the repository:

```bash
git clone https://github.com/berketonoz/Back-End-Development-Pictures.git
cd Back-End-Development-Pictures
```

2. Create a virtual environment:

```bash
python3 -m venv venv
source venv/bin/activate   # On Windows, use `venv\Scripts\activate`
```

3. Install the required packages:

```bash
pip install -r requirements.txt
```

4. Set up the database:

Ensure MongoDB is running and configured. Update the Django settings with your MongoDB connection details.

5. Apply the database migrations:

```bash
python manage.py migrate
```

6. Create a superuser:

```bash
python manage.py createsuperuser
```

7. Run the development server:

```bash
python manage.py runserver 8001
```

The application will be available at `http://127.0.0.1:8001`.

## Deployment

This microservice is deployed on Kubernetes with OpenShift and MongoDB. Follow these steps to deploy:

1. Install the OpenShift CLI:

Follow the instructions at [OpenShift CLI Installation](https://docs.openshift.com/container-platform/latest/cli_reference/openshift_cli/getting-started-cli.html).

2. Log in to your OpenShift account:

```bash
oc login
```

3. Create a new project (if not already created):

```bash
oc new-project your-project-name
```

4. Create a new application and link it to your MongoDB instance:

```bash
oc new-app your-docker-image --name=picture-microservice
oc create -f mongodb-deployment-config.yaml
oc set env dc/picture-microservice --from=secret/mongodb-secret
```

5. Expose the service:

```bash
oc expose svc/picture-microservice --port=8001
```

6. Access your application:

After deployment, your application will be available at the URL provided by OpenShift.

## Usage

- Access the admin interface at `http://YOUR_DEPLOYED_URL/admin` to manage pictures and users.
- Use the API endpoints to interact with the picture data programmatically.

## Running Tests

To run the tests, use the following command:

```bash
python manage.py test
```

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any changes.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/YourFeature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/YourFeature`)
5. Open a pull request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

Berketonoz - [GitHub](https://github.com/berketonoz)

Feel free to contact me if you have any questions or suggestions.
