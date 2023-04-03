# Workspace

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 15.1.3.


## Example to create a MicroFrontend.
- To create the base project thath includes the Shell and the Microfrontends, use the command ***ng new workspace --create-application=false***
- When finish the project creation, inside of the project we can start to create the diferents apps using the command ***ng g application shell --style=scss --routing=true***
-  ***ng g application mf-navbar --style=scss --routing=true***
- After create every project, we can create the diferents components, modules, etc in each project using the command  ***ng g c "component name" --project=shell*** or the destination project.
- Define the routes and the differents modules for every components to show ***(ng g module "module name" --project="project name" --routing)***
- once the creation process finished, we use the command ***ng add @angular-architects/module-federation --project shell --port 5000*** using the jost prohect name, in this case is "shell", and then define the port of integration to the differents microfrontends. This modify the angular.json and create *webpack* elements.
- Repeat the process for any microfrontend ***ng add @angular-architects/module-federation --project mf-navbar --port 4242***
- Inside the generated webpacks, we have to uncomment the lines according the project, if is host or remote.

### For mf projects
- In the webpack, change the filename for a relevant name to the project, and modify the module to expose, also include the rxjs dependency in "shared"
***rxjs: { singleton: true, strictVersion: true, requiredVersion: 'auto', includeSecondaries: true },***
- and now we can start the project ***ng s mf-navbar***

### For host project
- In the webpack, uncomment the code for host, and include or modify the Urls of the microfrontends. and add the dependency rxjs ***rxjs: { singleton: true, strictVersion: true, requiredVersion: 'auto', includeSecondaries: true },***
- Modify the app-routing of the host project to include the microfrontend like the app-routing.module od the shell project.
- Create a file ***declarations.d.ts*** to declare the different mf to include inside the routing.
- Finally execute the host project ***ng s shell***