# Casting agency By Zaid alwawi 

The motivation for this project is to create my capstone project for Udacity's Fullstack Nanodegree program.
It models a company that is responsible for creating movies and managing and assigning actors to those movies.
The assumption is that I am an Executive Producer within the company and wants to create a system to simplify and streamline my process process.


## Project dependencies

## Getting Started

### Installing Dependencies

#### Python 3.7

Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)


#### PIP Dependencies

```bash
pip install -r requirements.txt
```

This will install all of the required packages we selected within the `requirements.txt` file.

### open the app

- you may need to change the database url in setup.sh after which you can run
```bash
source setup.sh
```

- Start server by running
```bash
export FLASK_APP=app.py
flask run --reload 
```
or you can use 

python app.py



##### Key Dependencies

- [Flask](http://flask.pocoo.org/)  is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py.

- [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests from our frontend server.

- [Pycodestyle](https://pypi.org/project/pycodestyle/) - pycodestyle is a tool to check your Python code against some of the style conventions in PEP 8.


#### Authentication nad Token

Authentication is implemented using Auth0, it uses RBAC to assign permissions using roles, these are tokens you could use to access the endpoints.
Note: The tokens expires in 24 hours you can create your own tokens at [Auth0](https://auth0.com/). you would need to refelct this in auth.py
```py
AUTH0_DOMAIN = '<your auth domain>'
ALGORITHMS = ['RS256']
API_AUDIENCE = '<your api audience>'
```


### my auth0 sign in form 

This is my auth0 form [https://qoi.us.auth0.com/authorize?audience=casting&response_type=token&client_id=9xH60vLV4H6agCWmzT8szQuu2Er6J5qW&redirect_uri=http://127.0.0.1:5000/actors]


### users in auth0

I have three users in auth 0 

- ASSISTANT (get request only)
email = m@gmail.com 
pass = UAEt#2019

- DIRECTOR (get post and patch request)
email = a@gmail.com
pass = UAEt#2019


- PRODUCER (get request for both movie and actor also he can patch and post actor only)
email = z@gmail.com
pass = UAEt#2019



## Database Setup
The project uses Postgresql as its database, you would need to create one locally and reflect it in setup.sh.
To update the database and seed run the following :
```bash
python manage.py db upgrade
python manage.py seed
```


## Test 

I make a test file to test all the endpoint in my app.py file 
you can run test.py file by run 

this command 
'''
python test.py 

'''

### Endpoint 


## first (get request in movie) @app.route('/movies', methods=['GET'])
```json
{
    "movies": [
        {
            "id": 1,
            "release_date": "Mon, 06 May 2010 00:00:00 GMT",
            "title": "80 days arround the earth"
        },
        {
            "id": 2,
            "release_date": "Tue, 06 May 2003 00:00:00 GMT",
            "title": "second movie "
        }
    ],
    "success": true
}
```
## GET /movies/<int:id>

- can get the movie by id 

http://localhost:5000/2  

"movies" = {
    "id": 2,
    "title": "second movie",
    "release_date": "2020-2-20"
}


## POST /movies 

- can post movie 
`curl http://127.0.0.1:5000/movies -X POST -H "Content-Type: application/json" -d '{
	"title": "sample movie",
	"release_date": "2019-05-06"
}'`


## PATCH /movies/<int:id>

- patch the movie (update it)


## DELETE /movies/<int:id>

- delete the movie 



## first (get request in movie) @app.route('/movies', methods=['GET'])
```json
{
    "actors": [
        {
            "id": 1,
            "name": "zaid",
            "age": 30,
            "gender": "male"
        },
        {
            "id": 2,
            "name": "ali",
            "age": 40,
            "gender": "male "
        }
    ],
    "success": true
}
```
## GET /actors/<int:id>

- can get the movie by id 

http://localhost:5000/2  

"movies" = {
    "id": 2,
    "name": "zaid",
    "age": "30",
    "gender": "male"
}


## POST /actors 

- can post actors 
`curl http://127.0.0.1:5000/actors -X POST -H "Content-Type: application/json" -d '{
	"name": "zaid",
    "age": 20
	"gender": "male"
}'`


## PATCH /actors/<int:id>

- patch the actor (update it)


## DELETE /actors/<int:id>

- delete the actor 



## yes ! and thats all 
