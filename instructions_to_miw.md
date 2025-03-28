## Add values to env
```
REDASH_COOKIE_SECRET={{any_value}}
REDASH_SECRET_KEY={{any_value}}
REDASH_STATIC_ASSETS_PATH=/app/client/dist/
REDASH_FLASK_TEMPLATE_PATH=/app/redash/templates/
```

## Create database
`docker-compose run --rm server create_db`


## Run the service
`docker-compose -f compose.yaml up`

And wait for about 5 minutes. 
And you can access redash on 127.0.0.1:5001

## How to debug
Create launch.json in vs code with the following
```
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [

        {
            "name": "Python Debugger: Remote Attach",
            "type": "debugpy",
            "request": "attach",
            "connect": {
                "host": "localhost",
                "port": 5678
            },
            "pathMappings": [
                {
                    "localRoot": "${workspaceFolder}",
                    "remoteRoot": "."
                }
            ],
            "justMyCode": false
        }
    ]
}
```
Once you run `docker-compose -f compose.yaml up` , you should now debug the configuration in VS code by clicking the debug button. This will show the debug console docker service starting up

And now when you access http://localhost:5001, you can place breakpoints in your python code.