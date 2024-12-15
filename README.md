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

## Requirements

- Python 3.10
- Flask
- APScheduler
- SQLite (or any relational database of your choice)
- pyjwt 
## Endpoints 
#### auth/register ---(User will register using username, password)
Method: POST
Request :
```json
{
    "username":"dakshayani",
    "password":"sai"
}
Response :
```json
{
    "message": "User registered successfully"
}
```
#### auth/login ---(User will login using username, password)
Method: POST
Request :
```json
{
    "username":"dakshayani",
    "password":"sai"
}
```
Response :
```json
{
    "message": "Login successful",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6InBhbmR1cmFuYWEiLCJleHAiOjE3MzQyNjMxMTUsInVzZXJpZCI6Mn0.GeQDhi3fYgks38RwVTJt9EUCayxJw840rLF6Yya5bBY",
    "user_id": 2
}
```
#### trigger/create-trigger ---(User can create the trigger)
METHOD:POST
Request:
```json
{
  "trigger_type": "scheduled",
  "schedule_time": "2024-12-15T11:10:00",
  "interval": 30,
  "is_recurring": true
}
```
Resonse:
```json
{
    "message": "Trigger created successfully"
}
```
#### trigger/list-tiggers ---(User can list all triggers using the token authorization)
METHOD:GET
Response:
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
METHOD:POST
Respnose:
```json
{
    "message": "Event triggered successfully!"
}
```
#### trigger/test_trigger/1 ---(user can test trigger)
METHOD: POST

Respnose:
```json
{
    "message": "Test event triggered successfully!"
}
```
#### trigger/update-trigger/:id ---(user can updateTrigger)
METHOD:PUT
Request:
```json
{
  "schedule_time": "2024-12-15T11:00:00",
  "interval": 15,
  "is_recurring": false
}
```
Respnose:
```json
{
    "message": "Trigger updated successfully!"
}
```
#### trigger/delete-trigger/:id ---(user can DeleteTrigger)
Method:DELETE
Response:
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