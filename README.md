# Event Trigger System

This is a Flask-based Event Trigger System that allows users to create, list, update, delete, and manually trigger events. The system supports recurring and scheduled events, which can be triggered either on a defined schedule or on demand.

## Features

- **Create Trigger**: Create a new trigger for an event with specific parameters (time, interval, etc.).
- **List Triggers**: List all triggers associated with the authenticated user.
- **Update Trigger**: Update the details of an existing trigger.
- **Delete Trigger**: Delete an existing trigger.
- **Manually Trigger Event**: Trigger an event manually outside of its schedule.
- **Test Trigger**: Test a trigger manually to simulate the event execution.
- **Event Logs**: Event logs are maintained and can be archived or deleted based on their age.
- ** Application available in Docker image check below

## Context
1. Requirements
2. Endpints
3. Installation
4. Production Cost Estimation
5. Docker Image URLS and Commands
6. Application URLS
7. Reference
8. Frontend URLS and Repository

## Requirements

- Python 3.10
- Flask
- APScheduler
- SQLite (or any relational database of your choice)
- pyjwt 
## Endpoints 
#### auth/register ---(User will register using username, password)
###### Method: POST
###### Request :
```json
{
    "username":"dakshayani",
    "password":"sai"
}
```
###### Response :
```json
{
    "message": "User registered successfully"
}
```
#### auth/login ---(User will login using username, password)
###### Method: POST
###### Request :
```json
{
    "username":"dakshayani",
    "password":"sai"
}
```
###### Response :
```json
{
    "message": "Login successful",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6InBhbmR1cmFuYWEiLCJleHAiOjE3MzQyNjMxMTUsInVzZXJpZCI6Mn0.GeQDhi3fYgks38RwVTJt9EUCayxJw840rLF6Yya5bBY",
    "user_id": 2
}
```
#### trigger/create-trigger ---(User can create the trigger)
###### METHOD:POST
###### Headers: Authorization: Bearer <JWT_TOKEN>
###### Request:
```json
{
  "trigger_type": "scheduled",
  "schedule_time": "2024-12-15T11:10:00",
  "interval": 30,
  "is_recurring": true
}
```
###### Resonse:
```json
{
    "message": "Trigger created successfully"
}
```
#### trigger/list-tiggers ---(User can list all triggers using the token authorization)
###### METHOD:GET
###### Headers: Authorization: Bearer <JWT_TOKEN>
###### Response:
```json
{
    [
            {
        "api_endpoint": null,
        "api_payload": null,
        "created_at": "2024-12-15 09:45:38",
        "interval": 30,
        "is_recurring": 1,
        "schedule_time": "2024-12-15T11:10:00",
        "status": "active",
        "trigger_id": 12,
        "trigger_type": "scheduled",
        "user_id": 2
    }
    ]
}
```
#### trigger/trigger_event/:id ---(user can trigger event manually)
###### METHOD:POST
###### Headers: Authorization: Bearer <JWT_TOKEN>
###### Respnose:
```json
{
    "message": "Event triggered successfully!"
}
```
#### trigger/test_trigger/1 ---(user can test trigger)
###### METHOD: POST

###### Respnose:
```json
{
    "message": "Test event triggered successfully!"
}
```
#### trigger/update-trigger/:id ---(user can updateTrigger)
###### METHOD:PUT
###### Headers: Authorization: Bearer <JWT_TOKEN>
###### Request:
```json
{
  "schedule_time": "2024-12-15T11:00:00",
  "interval": 15,
  "is_recurring": false
}
```
###### Respnose:
```json
{
    "message": "Trigger updated successfully!"
}
```
#### trigger/delete-trigger/:id ---(user can DeleteTrigger)
###### Method:DELETE
###### Headers: Authorization: Bearer <JWT_TOKEN>
###### Response:
```json
{
    "message": "Trigger deleted successfully!"
}
```
## Installation
### Execution Manually 
1. Clone the repository and Local Execution:

```bash
   git clone https://github.com/saiguptha2003/EventTriggeringAPIv1
   cd event-trigger-system
```
2. Install Dependencies

```bash
python  -m install requirements.txt

```

3. python run Application

```bash
python app.py
```
### Execution using DockerFile

1. Create Image

```bash
docker build -t eventtrigger .
```
2. Create Container
```bash
docker run -d -p 5000:5000 eventtrigger
```
---
## Production Cost Estimation
#### Assumptions:
###### Cloud Provider: Render
###### Plan: Free tier for hosting + $7/month for custom domain and uptime guarantee
###### API Queries: 5 queries/day
###### Database: SQLite (no additional cost)
### Estimated Costs
##### Free Render Account  ----- Hobby Plan For hobbyists, students, and indie hackers.
##### $0 USD -- permonth
##### SSDs for $0.25/GB per month
##### Reder Hosting ------------------- Rs.0/-
##### Render Domain ------------------- Rs.0/-
##### Total --------------------------- Rs.0/-

---
## Docker Image URLS and Commands
#### Docker Hub URL :https://hub.docker.com/r/pandusa2003/eventtrigger
#### Command to pull Docker Image from DockerHub
```bash
docker pull pandusa2003/eventtrigger
``` 
---
#### FRONTEND REACT APP REPOSITORY URL : https://github.com/saiguptha2003/eventTriggerUI
##### Endpoints: https://github.com/saiguptha2003/eventTriggerUI
###### /register
###### /login
###### /triggers/create
###### /triggers/list
#### Postman : https://eventtriggering.postman.co/workspace/eventTriggering-Workspace~a4ae8fa1-8bd3-4fad-a535-7b6ef0a8d3e4/request/26910096-4991d1e6-ed87-4749-bfc1-de5e0feb76ab?action=share&creator=26910096&ctx=documentation&active-environment=26910096-7ce846b0-6f80-4635-841b-f58e3e9192c6

#### API URL: https://eventtriggeringapiv1.onrender.com/

##### https://eventtriggeringapiv1.onrender.com/auth/register
##### https://eventtriggeringapiv1.onrender.com/auth/login
##### https://eventtriggeringapiv1.onrender.com/trigger/create-trigger
##### https://eventtriggeringapiv1.onrender.com/trigger/list-triggers
##### https://eventtriggeringapiv1.onrender.com/trigger/trigger_event/:id
##### https://eventtriggeringapiv1.onrender.com/trigger/test_trigger/:id
##### https://eventtriggeringapiv1.onrender.com/trigger/update_trigger/:id
##### https://eventtriggeringapiv1.onrender.com/trigger/delete_trigger/:id


## Reference:
1. Google
2. Stack Overflow
3. Python Docs
4. APscheduler
5. YouTube for understanding triggers
6. Render Documentation
7. JWT documentation
8. ChatGPT to generating common templates
9. Claud AI for generating Go scripts for testing and managment
10. Copoilt used for generating React Application for the created API for simplicity and flexibility