<h1 align="center">Hi, guys! 👋</h1>

<p align="center">
    <b>What is InfraSetupApi?</b><br><br>
    <i>
        This software is designed to configure network devices using <span color="blue">Ansible</span><br>
        For now it works in a very simple way, but I plan to improve security and new features.<br>
        For more information, diagrams and project architecture, see our documentation.<br>
    </i><br>
</p>

## Table of Contents

- [Setup](#setup)
- [Secret Key](#secretkey)
- [Configure your .env](#configure-env)
- [DataBase](#database)
- [Version](#version)
- [Videos](#videos)


## Setup

#### You can use Docker Image

```
docker pull kekinho/infrasetup:latest
docker run -p 8000:8000 --name infrasetup -d kekinho/infrasetup:latest
If dont work:
sudo docker run -p 8000:8000 kekinho/infrasetup:latest
```

After creating the image, use for login:
```
Username: admin
Password: 123
```

Once inside the system, you have the capability to manage your users and their credentials effectively.

#### You can use Git Clone

To set up the project locally, please follow these steps:

1. Clone the repository: `git clone https://github.com/Kekinho/InfraSetup.git`
2. Install the for ansible and Django in requirements.txt .
3. You need generate your own [Secret Key](#SecretKey).
4. [Configure your .env](#configure-.env)
5. You can run it in [your terminal or dockerfile](#run-infrasetup)


## SecretKey

Start the **Python interpreter**
```
import secrets
secrets.token_hex(32)
Copy the key in .env
```
Be mindful that you can generate a new key whenever necessary. 
However, it is crucial to remember that if you are using our project, you should not disclose the key to anyone.

## Configure .env

Create an .env file in the /core directory:
```
SECRET_KEY=SECRET KEY
DEBUG=True
```
**Use DEBUG=TRUE only when in development.**

## Run InfraSetup

#### Terminal Local:

```
cd WebApi
python manage.py migrate
python manage.py runserver
```

#### Dockerfile:

```
cd WebApi
python manage.py migrate
cd ..
docker build -t image_name
docker run -p 8000:8000 image_name

```
## Database

We use SQLite at first, but it is possible to manage other databases.

Use [Django's](https://docs.djangoproject.com/en/4.2/ref/databases/) own reference.

If you lose the database file or decide to switch to a different one, you will need to follow these steps:

1. Migration ( **Inside the WebApi file** )


```
python manage.py migrate
```

After this, a new admin user with the username "admin" and password "123" is automatically created.

## Version


| Version   |            |  Date |
|----------|:-------------:|------:|
| 1.4 |  Fixed ansible conection | 17/07/2023 |
| 1.3 |  SSH Save Credentials | 16/07/2023 |
| 1.2 |  User Options | 14/07/2023 |
| 1.1 |  Fixed login form | 14/07/2023 |
| 1.0 |    Up version 1.0   |   14/07/2023 |


## Videos


[First impression ( 14/07/2023 )](https://www.youtube.com/watch?v=5jByei5CKC8)
