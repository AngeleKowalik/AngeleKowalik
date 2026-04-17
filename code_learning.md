# List of usefull things learnt
## Git:
### Setup:
- Inside root folder powershell terminal : `git init`
- Add desired files / folders (still in powershell) : `git add file_name.suffix`
- To ignore specifics files / folder, need to create a .gitignore file, and specifies
files to be ignored.

### Usage
#### Saving your changes:
- Save the files you've worked on
- Go to the control tab in vs code
- Stage changes (`+` sign) 
- Apply a name to your changes (message box)
- Press commit

## Virtual environnment:
### Creation
- Open folder project terminal : right click on folder \ Open in Integrated Terminal
- Creating the VE : py -m venv .venv
- Opening / reopening a project : .venv\Scripts\activate
- Closing a project : deactivate

### Git and virtual environnement:
- .venv folder need to be ignored by git
- Create a requirement.txt file with all the -pip to include in the VE
- To create the list in cmd: pip freeze > requirements.txt 
- To install from the list in cmd: pip install -r requirements.txt 

## Modules:
### Fast API:
documentation: https://fastapi.tiangolo.com/tutorial/path-params/#create-an-enum-class 

#### Vocab:
##### Endpoint / path / route
Url used to access a part of a website

##### Backend
Thinking part of a programm, can be python for example

##### Frontend
Part of a programm that is displayed to the user like buttons, pictures, etc

##### API
The API is the thing in charge of the communication between the backend and the frontend


#### Installation : 
- In cmd : py -m pip install "fastapi[standard]"
- In python : from fastapi import FastAPI                                               
        
#### Initialization:
- Creating an instance of the object FastAPI in python : app = FastAPI() 
- Running the server :  
    - Launch the programm
    - In the console, type : fastapi dev main.py

#### Usage:
##### Endpoint:
###### Basic usage:
- Basic url used to access a specific part of a website
- Used to organize a website in distinct parts
- exemple : http://127.0.0.1:8000/url-to-access
- To create one : 

```python
@app.get("/url-to-access/")
def variable():
    return 'Test home page'
``` 

###### Endpoint commands type / HTTP Methods / HTTP Verbs:
- GET : fetch / read data from an endpoint : `@app.get('/username-base/user-1/')`       (viewing a user profile)
- POST : create data : `@app.post('/username-base/user-1/')`                            (submitting a new user)
- PUT : update data : `@app.put('/username-base/user-1/')`                              (changing username)
- DELETE : delete data : `@app.delete('/usernambe-base/user-1/')`                       (removing an user)

###### Parameter usage: 
- A parameter is something that will be entered in the website and be given to the backend
- For exemple here, the last part of the url will be returned:
- It is usefull to display a particular page such as the profile page of one user

```python
@app.get('/get-username/{user_name}')
def get_username(user_name: str = Path(
    description='Enter the city you want to search in the database'
    )):
    return user_name                                                                    
```

- After the first argument's parenthesis we can use:
    - `...` to make the argument mandatory
    - `None` to make the argument non mandatory

##### Query:
- A query is a thing add after the end of an url / endpoint, it starts with a `?`
- Used to perform search operation
- Display all the data but sorted (for example, a list of name sorted alphabetically)
- exemple : `http://127.0.0.1:8000/url-to-access?variable=value`

```python
@app.get('/get-username/')
def get_username_sorted(
    sorting_type: str = Query(description='Enter a sorting type')
    ):

    if sorting_type == 'alphabetically':
        return sorted(username_list)
```

## .md files:
- Are displayed well on github with "mise en forme"
- Can be exported well as pdf files
- Are usefull with the quick navigation outline from vscode 

## Interesting things to learn next:
- Predefined values in fast API using an Enum class (check the official doc)