# List of usefull things learnt

## Summary:
- [Markdown files guide](#md-files-and-how-to-work-with-them)
- [Virtual environnment](#virtual-environnment)
- Need to be updated
## Coding good practices:
### General
- DRY : don't repeat yourself -> if more than 3 time, put in a function
- Single responsibility principle -> each function should do only one thing and be as 
  modular as possible
- Naming : action verbs for function, noun for variables, be as descriptive as possible
- Name litteral number in form of constants at the beginning of the code so they can be 
  changed easily
- Never put an input() inside a function
- Log frequently so its easier to debug afterward
- Catch errors at the beginning of each functions

### Python
- Always use virtual environnement so python doesn't break or get messy
- Use type hinting extensively
- Always wrap executable block into `if __name__ == '__main__'`

## Usefuls keyboard shortcuts:
### General
- `ctr + f` -> Search for a word in a page
- `ctr + s` -> Save a file
- `ctr + x` -> Cut the selection
- `ctr + v` -> Past the selection
- `ctr + c` -> Copy the selection 
- `ctr + z` -> Undo last action
- `ctr + a` -> Selection all

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
##### To make name:
- Follow the rule  (if applied this commit will...) add method to make commit
- Create a title max 50 characters
- Leave blanck line
- use `-` and then write you have done and jump a line, repeat
- Press commit

##### Example:
```
Document BeautifulSoup module usage and refactor the rest of the document:

- Add BeautifulSoup module explanation and example
- Add a Linux / Mac section yet to be filled
- Clarify specificities of Windows code in powershell
- Fix indentation error in code's examples
- Update FastAPI import errors
```

## Virtual environnment:
### Creation
#### Under Windows
- Open folder project terminal : right click on folder \ Open in Integrated Terminal
- Creating the virtual environnement : py -m venv .venv
- Opening / reopening a project : .venv\Scripts\activate
- Closing a project : deactivate

#### Under Mac / Linux

### Git and virtual environnement:
- .venv folder need to be ignored by git
- Create a requirement.txt file with all the -pip to include in the virtual environnement
- To create the list in cmd: pip freeze > requirements.txt 
- To install from the list in cmd: pip install -r requirements.txt 

## Built-in python:
### Operators:
#### Arithmetics:
- `+` -> addition
- `-` -> substraction
- `*` -> multiplication
- `/` -> division
- `//` -> floor division (donne le reste de la division)
- `%` -> modulo (count until number on the left is reached then restart at 0)
- `**` -> exponantial (square, cube, etc)

#### Assignement operators:
- `=` -> assign the value on the right to the string on the left
- `+=` -> same as reassigning a value to itself and adding something to it
  can be done with any arithmetic operator : 
  ```python
  variable_1 = 5
  variable_1 -= 5
  print(variable_1)
  # variable_1 is equal to 0
  ``` 

#### Comparison operators:
Returns a boolean
- `==` -> True if left is equal to right
- `!=` -> If different from equal
- `>` -> Left is greater than right
- `<` -> Left is smaller than right
- `>=` -> Left is greater or equal to right
- `<=` -> Right is smaller or equal to right

#### Logical operators:
- `and` -> True if both statements are True
- `or` -> True if at least one statement is True
- `not` -> Revert the result

#### Identity operators:
- `is` -> Return True if both variables are the same object
- `is not` -> Return True if variables are not the same object

#### Membership operators:
- `in` -> Returns True if a sequence with the specified value is present in the object
- `not in` -> Returns True if a sequence with the specified value is not present in 
  the object

### Loop:
- `while True` -> allow to repeat a part of a program indifinately
- `while variable < variable2` -> repeat until condition is met

### dictionary
A dictionary is a repertory of key : value pair. When calling a key, it returns its
pair value. 

A key is a string but the value can be of any type even list or other dictionaries

- Creating a dictionary
  ```python
  dictionary = {
    'key 1' : 'value 1',
    'key 2' : 'value 2'
    }
  ```

- dictionary comprehension iterate through the dictionary and do an action on each
  key : value pair
  `key:  value for key, value in dictionary.items() if value`

- `example_dictionary.get(user_input.lower(), 'Invalid key')`-> Try to find the first 
  argument in the dictionary key list, if not found, return the second argument

### List
A list in an ensemble of multiple items of any type, even an other list

- Creating a list :
  ```python
  example_list = [
    object_1, 
    object_2
  ]
  ```

### Handling errors:
- Allow to handle errors without crashing the program, also help to diagnose errors
  ```python
  try:
    print(int('un'))
  except Exception as error:
    print(error)
  ```

## Modules:
### Standard library:
#### Webbrowser:
##### Initialization:
- `import webbrowser` -> Import the module

##### Usage:
- `webbrowser.open(str(PATH_EXAMPLE.absolute()))` -> Open in a new window or in browser
  the file located in the path. 

#### Pathlib:
Pathlib is used to write clearer, more concise and portable pathes

##### Initialization:
- `import Pathlib` -> Import the module
- `from Pathlib import Path` -> Import most useful function
- `PARENT_DIRECTORY: Path = Path(__file__).parent` -> Define file as root directory

##### Usage:
- `TEST_DIRECTORY = PARENT_DIRECTORY/'test.py'` -> Define a path to a specific file
- `print(TEST_DIRECTORY.absolute())` -> Show the all path instead of the relative one.
  Mandatory when working directly with the OS, else not needed.

##### Example:
```python
PARENT_DIRECTORY:Path = Path(__file__).parent
README_PATH: Path = PARENT_DIRECTORY/'README.md'
# Open the specific file in a new window
webbrowser.open(str(README_PATH.absolute()))
```

#### Logging:
Logging is a tool used to make your code cleared and easier to debug. It is good
practice to log your code as you build it.

While building your code, you can log in your console but once your app is released, you
should log in a separate text file

### Usage
- `import logging` -> import the module logging
- To initialize it: 
  ```python
  logging.basicConfig(
    level=logging.DEBUG,
    format= '%(asctime)s - %(levelname)s - %(message)s'
    )
  ```
  Specify in `level=logging.` which one you want to see (you see all logs up to that 
  level) : CRITICAL > ERROR > WARN > INFO > DEBUG > NOTSET 


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
- Under Windows, in powershell : py -m pip install "fastapi[standard]"
- In python : import fastapi                                               
        
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
def get_username(user_name: str = fastapi.Path(
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
    sorting_type: str = fastapi.Query(description='Enter a sorting type')
    ):

    if sorting_type == 'alphabetically':
        return sorted(username_list)
```

### Requests:
#### Installation:
- Under Windows in powershell : `pip install requests`
- In python : `import requests`

#### Usage:
- Creation of a response object : `response = requests.get(http://test-url.com)`
- Creating a json dictionary from a response object : `dictionary = response.json()`

##### Response's object attributes:
- `response.status_code` -> if 200 : valid response
- `response.json()` -> return a json dictionary
- `response.text` -> retur a string

#### Anti-bot work around:
Sometimes when scrapping, anti-bot tools will flag you and ban your ip
To avoid that, there are multiple tools at disposition:
- Selenium : non bannable, open a real webpage (but is slow)

#### Code example:
```python

import requests

base_url = 'https://pokeapi.co/api/v2'

def get_pokemon_info(name):
    url =   f'{base_url}/pokemon/{name}'
    response = requests.get(url)

    if response.status_code == 200:
        pokemon_data = response.json()
        return pokemon_data
    
    else:
        print (f'Failed to retrieve data {response.status_code}')

while True:
    print('Enter a pokemon name')
    pokemon_name = input()
    pokemon_info = get_pokemon_info(pokemon_name)
    if pokemon_info:
        print(f'Name: {pokemon_info['name']}')
        for type in range(len(pokemon_info['types'])):
            print(f'Type: {pokemon_info['types'][type]['type']['name']}')
        
        print(f'Weight: {pokemon_info['weight']}')
```


### Beautiful soup:
Need to also use requests' module

#### Vocab:
- A parser is something taking an html string and translating it to a nested structure

#### Installation:
- Windows : In powershell : `pip install beautifulsoup4`
- Windows : In powershell, need to install a parser, one good choice is : `pip install lxml`
- In python : `import bs4`
- In python : `import lxml`

#### Usage:
- To create the soup : `soup = BeautifulSoup('html page as a string', 'parser as string')`
- To make the soup more readable : `print(soup.prettify())`
- To return the first appearance of a tag : `soup.find('tag as string')`
- To return all appearance of a tag as a list : `soup.find_all('tag as string)`
- To print only the text without tags : `soup.text`

#### How to work with html ?
- Online, right click > `Inspecter l'élément`
- Left upper corner in the new opened tab (dotted square with arrow) > 
  `Select an element in the page to inspect it` -> allow to hover over element to 
  pinpoint their html code
- Network tab > clear network > Fetch/XHR > click on desired component -> allow you to 
  spot which file is called (for example, when a button is pressed)


#### Example:
```python

from bs4 import BeautifulSoup
import requests
import lxml

url = 'https://motherfuckingwebsite.com' 

response = requests.get(url)
response_text = response.text

if response.status_code == 200:
    soup = BeautifulSoup(response_text, 'lxml')
    print(soup.prettify())
    title = soup.find('h1')
    print(title.text)
    
else:
    print(f'Unable to return data {response.status_code}')
```

## API:
### recherche d'entreprise.gov:
- main page -> https://recherche-entreprises.api.gouv.fr/docs/
- swagger page -> https://petstore.swagger.io/?url=https%3A%2F%2Frecherche-entreprises.api.gouv.fr%2Fopenapi.json
Allow to search for companies based on:
    - NAF code
    - Postal code
    - Number of employees
    - etc

#### How to use:
- 7 requests max per seconds
- If too many requests -> HTTPS 429 - Too Many Requests
  Retry-After -> delay before next request

## .md files:
- Are displayed well on github with "mise en forme"
- Can be exported well as pdf files
- Are usefull with the quick navigation outline from vscode 

### How to use:
- Creating bullets point : `-` / `+` / `*` 
- Creating foldable (only in vscode) title: `#`, `##`, `###`, etc...
- Creating code line : ` `
- Creating code box (need to jump a line after opening and before ending) : 
```python
print('random code')
```

# Interesting things to learn next:
- Predefined values in fast API using an Enum class (check the official doc)
- Learn playwright instead of selenium for complex scraping tasks
