Fitsync is a python app that syncs data between Fitbit and Google Fit.

Currently, it only copies weight data from Fitbit to Google.

## Setup

### Environment

Use `virtualenv` to create an environment to install required packages,

    $ virtualenv env

Activate the environment in your shell,

    $ source env/bin/activate

Use `pip` to install the required packages,

    $ pip install -r requirements.txt

### Google Credentials

[Create a project in Google Developers Console and enable the fitness API](https://console.developers.google.com/flows/enableapi?apiid=fitness). Note the client id and client secret.

Run `auth_google.py` to get credentials for write access to a user's body data,

    $ python auth_google.py [YOUR CLIENT ID] [YOUR CLIENT SECRET] https://www.googleapis.com/auth/fitness.body.write

This script opens a browser window where you can log in to your Google account and authorize the app to "View and store body sensor data in Google Fit". When you accept, the script writes the credentials to a local file named `google.json`.

## Usage

Run `fitsync.py` to download data from Fitbit and upload to Google,

    $ python fitsync.py

Use the `delete` command to remove data from Google,

    $ python fitsync.py delete

Use the `get` command to see the data stored in Google,

    $ python fitsync.py get

## See your data

To view weight data on [Google Fit](https://fit.google.com),

1. Choose "See graph details" for any day
2. Choose "+ Add chart" 
3. Choose "Weight"
4. Choose "Day", "Week", or "Month" to see the data for that time period
