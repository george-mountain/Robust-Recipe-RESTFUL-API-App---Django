# Robust Recipe RESTFUL API App Using Python Django

This is a repository for a classical RESTFUL recipe api application using python django

### Tools used for the developement
##### python, Django, DJANGO REST FRAMEWORK (DRF), Docker, Nginx, uwsgi


### Application Development methodology

#### Test Driven Development (TDD)
In this development practice, we start by writing a test that test the functionalities that we want to add/implement followed by writing our implementation codes that passes the test we wrote

![image](https://user-images.githubusercontent.com/19597087/215330496-66de3aa5-4136-48c0-af96-087c2bee9678.png)

### WHY USE DOCKER?

It helps to ensure consistent development and production environment
Easier collaboration,
Capture all dependencies as code such as python requirements, operating system dependencies etc
Easier cleanup.

### DRAWBACKS OF USING DOCKER
	1. VSCode unable to access interpreter
	2. More difficult to use integrated features
	3. It is suggested to use terminal in running debugging and linting to our projects.

### How we will use Docker in this project

	1. Define Dockerfile: The docker file will contain all the operating system level dependencies that our project needs.
	2. Create Docker Compose configuration: This tells Docker how to run the images that are created from our Docker file configuration
	3. Run all commands via Docker Compose

![image](https://user-images.githubusercontent.com/19597087/215331055-512b4a16-b8c6-42ca-a1f6-86ce4c1e1858.png)

### CONFIGURE DOCKER WITH DJANGO

	1. CREATE A DOCKER FILE: We start by defining a Docker file that has all of the operating system level dependencies level needed for our project.
	2. Lists steps for creating image: Docker file is simply just a list of steps that Docker uses to create an image for our project.
	Choose a base image (python in our case): We are going to use the python base image that is provided for free on Docker Hub.
	Install Dependencies: These are operating system level dependencies
	Setup Users: These are the Linux USERS that are needed to run our application and these users are created inside our docker container.
	

### DOCKER Compose
	- Docker compose defines how Docker images should be used to run out development server.:
	- Defines our "Services": You basically define the images as different services and every service has a name. Example
	Name(e.g app)
	Port mappings
	Volume mappings: Volume mappings is important because it how the code in our project gets into the Docker container.

USAGE of the Docker Compose after Setup

	1. Run all commands through Docker Compose: We are going to run all of the commands through Docker Compose and the commands are going to look like the one shown below
	docker-compose run --rm app sh -c "python manage.py collectstatic"
	2. You start by typing docker-compose which will run the Docker Compose application.
	3. "run" in the command above will start a specific container defined in config
	4. "-- rm" in the above command removes the container. It is optional. However, it tells Docker compose to remove the container once it is finished running. It is recommended that you add this any time you are running a single command so that you don't have a buildup of lingering containers on your system.
	5. "app" is the name of the service. This is the name of the app that you defined inside your Docker compose configuration. In our case, the app that we are going to be using is going to be called "app"
	6. "sh -c " in the above command passes in a shell command. This is the command that is going to be passed into the container when it runs. This command basically says we want to run a single command on our container.
	7. Finaly passing the command to run inside the container. In our own case, the command to be run is python manage.py collectstatic. Note that it shoud be on quotation as seen in the above command.
  
### Configuring Docker compose in production

![image](https://user-images.githubusercontent.com/19597087/215331105-9a97643d-b4ab-4a4d-9b44-5bb4a32d0ff8.png)


### CREATING THE DOCKER FILE

The docker file can be created as shown below

![image](https://user-images.githubusercontent.com/19597087/215330729-07729b9f-89d2-495c-8c6d-fe48823c675e.png)


TESTING IN DJANGO

Django has something called called the Django Test Framework, which is built into django. We will use this to write the unit tests in this project.

Django Test Framework is based on the unittest library. The unit test library comes out of the box with python but Django test framework adds some additional features to this library that is useful when testing Django projects.


DJANGO TEST FRAMEWORK
	- Based on the unittest library
	- Django adds features
	Test client - dummy web browser
	Simulate aunthentication
	Temporary database
	- Django REST Framework adds features
	API test client




### API Documentation

#### WHAT TO DOCUMENT

	1. Everything needed to use the API
	2. Available endpoints (paths)
	3. Supported methods such as GET, POST, PUT, PATCH, DELETE
	4. Format of payloads (inputs) such as the parameters, or the paramters for posting data (like POST JSON FORMAT)
	5. Format of responses (outputs): Response JSON format
	6. Authentication process
	
	

#### OPTIONS FOR DOCUMENTATION

	- MANUAL METHOD
	Word doc, Markdown etc
	- Automated: Using metadata from the code that you create and aslso comments that you add to the python code that you create. Use that metadata to generate the documentation pages automatically for your API.
	
	
#### AUTOMATED DOCS WITH DJANGO REST FRAMEWORK (DRF)

DOCS IN DRF
	- Auto generate docs (with third party library) - drf-spectacular
	- Generate Schema
	- Browsable web interface (make test requests, Handle auth)
	
Auto generate docs (with third party library) that allows you to auto generate the documentation for DJANGO RESTFUL FRAMEWOR API. The library is called the DRF Spectacular (drf_spectacular) Library or Django Rest Framework Spectacular

#### HOW IT WORKS

	1. Generate "Schema" file: This will be accessible at an endpoint and essentially, you go to the endpoint and it will download the file .
	2. Parse Schema into GUI: and the graphical user interface will open or parse the schema file and this will be able to generate a graphical user interface that allows you to make actual requests and display the information as in the schema.
	
	
	#### OpenAPI Schema
	1. Standard for describing APIs
	2. Popular in industry
	3. Supported by most API documentation tools
	4. Uses popular formats: YAML/JSON
	
	
	
	
#### USING A SCHEMA

	1. Download and run in local Swagger instance: You can download it straight from your API after you deploy it, and you can run it in a local swagger instance or another swagger instance on the internet
	2. Serve Swagger with API: we are going to be serving swagger with our API itself. So, there is actually going to be a deployed URL as part of our API that allows you to load the swagger documentation and use it in real time.









