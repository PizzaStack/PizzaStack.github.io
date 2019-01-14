# Angular
## Requirements
To build an Angular application, you will need Node.js and the Angular CLI tool. Installing Node.js will also install `npm`, the Node Package Manager which you can use to install Angular CLI:
>npm install @angular/cli -g

The `-g` flag will install the tool globally, so don't forget it! Use `ng -v` to check that you have Angular CLI correctly installed.

## Getting Started
To begin a new project, use the `ng new` command:
>ng new yourApp

This creates a `yourApp` folder with a bootstrapped Angular project ready to go. To test it out, enter the project directory and then run:
>ng serve

This bundles and deploys the application onto a development server at `localhost:4200`.

Angular bootstraps an App Module and an App Component for you to start, but you can start generating new components, services, and routes with the `ng generate` command.
>ng generate component your-component

Or `ng g c your-component` for short.

To generate a service, use:
>ng generate service your-service
