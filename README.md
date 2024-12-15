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

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/event-trigger-system.git
   cd event-trigger-system
