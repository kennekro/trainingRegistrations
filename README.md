# training-registration
A simple Vue application for registering my workout routine. The goal here is to create a simple frontend hosted as an Azure web application, where the data is sent to some kind of storage. 

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```
The build command needs to be run before pushing the changes to origin/master in order to update the /dist folder used by Azure.

### Hosting in Azure
1. Create a web application
2. Specify conneciton to GitHub in the Deployment Centre of the web application
3. Change the virtual path of / from site\wwwroot\  to site\wwwroot\dist

### Todo
- Decide where to host the registration data
- Send the registration data to the storage solution
- Expand the application to fetch information from the storage, and display information about my latest registrations