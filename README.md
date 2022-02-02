# BlazorWASMHosted_CRUD_B2C
This project is a demo of how to build a .NET web application, usinga Hosted Blazor WASM. The API (Server App) and the Client app are hosted together. Both applications use Azure B2C for authentication/authorization. On the initial startup of the application, be sure the DB is correctly created. You will need MSSQL Server installed (I use MSSQL Developer Edition). Assuming the connection string is correct in appSettings.json, the application should create the DB on startup.

### Setup:
Clone the repo. To run the application, you need to run both the API and the Blazor app. If you have a cors issue, ensure the port used in Startup.cs is the same as the port the client app is running on.

The Azure B2C settings are set in the appSettings.json files. This public repo does not include those values - set those values using your specific Azure B2C values/id's.

### DB Migration Commands:
Add-Migration -Project BlazorWASMHosted_CRUD_B2C.Data -StartupProject BlazorWASMHosted_CRUD_B2C.Server -Name InitialCreate

Update-Database -Project BlazorWASMHosted_CRUD_B2C.Data -StartupProject BlazorWASMHosted_CRUD_B2C.Server

### Ignore Local Changes to AppSettings.json:
Sensative configuration data, such as the DB connection strings, or Azure B2C config to the appsettings.json files. AppSettings existin the API and Web projects. Do not check in these values to the repo. Use the following commands to ignore changes to the appsettings.json files:
 - git update-index --assume-unchanged .\BlazorWASMHosted_CRUD_B2C.Server\appsettings.json            
 - git update-index --assume-unchanged .\BlazorWASMHosted_CRUD_B2C.Client\wwwroot\appsettings.json
 - use '--no-assume-unchanged' to reverse the ignore.
