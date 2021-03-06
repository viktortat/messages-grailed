# Messages - Grailed
RESTful API that allows users to send messages to one another

## Installation
```bash
# Clone the repository
git clone git@github.com:djstein/messages-grailed.git

# Create a virtualenv
virtualenv -p python3 venv

# Activate the virtualenv
source venv/bin/activate

# Install the pip requirements
pip install -Ur requirements/local.txt

# Runserver
python manage.py runserver
```

Once running open the API at [localhost:8000](http://localhost:8000)
View the data in JSON format by appendning ```http://localhost:8000/?format=json```
Or by clicking the dropdown on the GET and clicking json

## Example Data
There is already a set of example data and users.
Users:
- Username: Admin Password: admin1234
- Username: tricky_rick Password: geobaskets
- Username: test Password: test1234

View their messages!

## Using Terminal Commands
In a second terminal that is not the server running, activate the virtualenv to make requests at the API.
Use [Curl](https://curl.haxx.se/)  in the terminal to access the API (demonstrate its availablity through Web Applications, React Native, etc).
```bash
# Login test user
curl -X POST -d "username=test&password=test1234" http://localhost:8000/login/

# You will get an authentication token back! Use this format to make other commands!
curl -H 'Accept: application/json; indent=4' -H 'Authorization: JWT <token>' http://localhost:8000/channels/1/
```

## API Explination
This API does the following:
- register Users
- login Users  -> you will recieve a [JSON Web Token](https://jwt.io/) which will be used in a JavaScript conole with Authentication or in a web framework AJAX request (ie. [Axios](https://github.com/mzabriskie/axios))
- logout Users -> deletes any active web tokens for a User's session
- create/update/delete Channel for Messages between N number of Users
- create Message by a User that is added into a Channel

There are a number of permissions that restrict access/deletion/updating to data.
View the entire database schema at [localhost:8000/schema](http://localhost:8000/schema)

One can either follow the API Urls or provide data through a JavaScript console (inside of the browswer based or a terminal emulator).


### Registration
POST to Register: [localhost:8000/login](http://localhost:8000/registration)


### Login | Logout
POST to Login: [localhost:8000/login](http://localhost:8000/login)

GET or POST to Logout: [localhost:8000/login](http://localhost:8000/logout)


### Users
GET User List: [localhost:8000/users/](http://localhost:8000/users/)

POST to create User: [localhost:8000/users/](http://localhost:8000/users/)

GET User Detail: [localhost:8000/users/1/](http://localhost:8000/users/1/)

POST/PATCH to update User Detail: [localhost:8000/users/1/](http://localhost:8000/users/1/)

DELETE to detele User Detail: [localhost:8000/users/1/](http://localhost:8000/users/1/)


### Channels
Make a Channel and add Users to it so they can add Messages

GET Channel List: [localhost:8000/channels/](http://localhost:8000/channels)

POST to create Channel: [localhost:8000/channels/](http://localhost:8000/channels)

GET Channel Detail: [localhost:8000/channels/1/](http://localhost:8000/channels/1/)

POST/PATCH to update Channel Detail: [localhost:8000/channels/1/](http://localhost:8000/channels/1/)

DELETE to detele Channel Detail: [localhost:8000/channels/1/](http://localhost:8000/channels/1/)


### Messages
GET Message List: [localhost:8000/messages/](http://localhost:8000/messages)

POST to create Message: [localhost:8000/messages/](http://localhost:8000/messages)

GET Message Detail: [localhost:8000/messages/1/](http://localhost:8000/messages/1/)
