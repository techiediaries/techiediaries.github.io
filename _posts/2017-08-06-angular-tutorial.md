---
title: Full-Stack Angular 6 Tutorial Series
date: 2017-08-06 00:00:00 Z
tags:
- django
- angular
layout: blog
summary: Learn Angular 6 by building a full-stack web application
image: "/images/blog/blogging-again.png"
---

Angular 6 Tutorial Series (JWT Auth, RxJS 6, HttpClient, Bootstrap 4, Material Design, Routing and Forms)
In this Angular 6 tutorial series for beginners, we'll see by example how to build an Angular 6 full-stack application with CRUD functionalities and JWT authentication. We'll see how to use the Angular 6 CLI to generate a front-end application, how to generate and work with Angular 6 components and services. We'll learn about Angular 6 routing - setting up Angular 6 router and creating routes and outlet(s) etc. - and also forms - both dynamic and template based forms- We'll also learn about how to consume RESTful APIs using Angular 6 HttpClient and RxJS 6 Observables. Finally, we'll see how to use Angular Material to create the application UI but if you prefer to use Bootstrap 4, we'll also see how to integrate Bootstrap 4 with Angular 6.
Angular 6 Tutorial Series for BeginnersYou can also follow the original version of this tutorial.
By the end of this tutorial series with Angular 6, you'll learn about the following topics:
How to upgrade or migrate an Angular 5|4 to Angular 6
How to create an Angular 6 front-end project or application using Angular CLI 6
How to generate components and services using Angular CLI 6
How to add component routing using Angular 6 Router
How to create forms using Angular 6 forms module
How to consume a RESTful API using Angular 6 HttpClient
How to send Post, Get, Put and Delete http requests and create an Angular 6 CRUD example
How to create the UI using either Bootstrap 4 or Angular 6 Material Design
How to add JWT authentication to your Angular application
How to use RxJS 6 for Observables and Reactive programming

Upgrading/Migrating your Angular 5 Project to Angular 6
In case, you already have a project with Angular 5 and you want to migrate to Angular 5, make sure to read the tutorial guide next, which shows you how to update Angular and Angular CLI to the latest version - Angular 6 - and upgrading existing projects to use the new version. Read the full tutorial to upgrade to Angular 6.
Upgrading RxJS 5 to RxJS 6 in Angular 6 Project
RxJS 6 is the latest version for the RxJS library of reactive programming. This version has many breaking changes with RxJS 6. So if you are upgrading your Angular 5 project to Angular 6, you'll also need to make sure your updating RxJS. Thanks rxjs-compat a compatibility layer for RxJS 5, you will still be able to run your old RxJS 5 code in Angular 6 but eventually you'll have to use the new RxJS 6 APIs. You can take a look at this tutorial for a guide on how to upgrade Angular 6 to RxJS 6.
Angular 6 New Features
Angular 6 has a plethora of new features and additions. Let's see the most important features:
Angular CLI 6 New Powerful Commands
The Angular CLI v6 brings many powerful commands:
ng add: You can use this command to quickly add and setup new libraries. For example, the well known libraries like Angular Material 6 or Bootstrap (via ng-bootstrap) can be installed without manually adding any configurations. As an example, to add Bootstrap to your project. Simply run the following command from your terminal:

ng add @ng-bootstrap/schematics
If you are a library developer, you can also use Angular 6 Schematics to create schematics for your libraries so developers can install them via ng add.
ng update: Using this command, you can easily update your Angular 4|5 packages to Angular 6. And you can also use Schematics to make it easy to integrate third-party libraries with ng update.

New Angular CLI Configuration File
In Angular 6 projects - generated with Angular CLI 6 - the configuration file .angular-cli.json is replaced by angular.json - the overall structure of angular.json has also changed.
You Angular CLI 6 project is organized as a workspace that contains multiple applications with a default application. You can have multiple applications per one project and you can also have libraries as a part of the project (ng g library).
Angular 6 Schematics
Schematics provides a powerful work flow tool for Angular 6 - You can use them to apply transforms to your project, for creating new components and adding libraries. By taking advantage of Angular Schematics, you can build your own frameworks - for boosting productivity- on top of your projects.
New Angular 6 Renderer Ivy
A new renderer called Ivy was created by the Angular team. Ivy is capable of producing smaller bundles that you can compare in size with small libraries such as Preact for example. Ivy is still experimental in Angular 6 so for now you need to enable it using a configuration option in your project.
Angular 6 Elements
Angular 6 brings a new library - called Elements, you can use Angular Elements to transform your Angular components to standard web components - also known as custom elements - supported natively in modern web browsers such as Chrome, Firefox and Edge etc. You can re-use your Angular 6 components everywhere - from Angular to other libraries like React, Vue or just vanilla JavaScript.
Support for TypeScript 2.7
Angular 6 depends on TypeScript 2.7 which brings new features and capabilities.
Support for RxJS 6
Angular 6 depends on RxJS 6 instead of RxJS 5 - for working with Observables and other Reactive programming operators - RxJS 6 has breaking changes and features like new import paths, tree-shakablility which helps produce smaller Angular bundles.
Getting Started with Angular 6 - Generating a New Angular Project with Angular CLI v6
You can get started developing Angular 6 project by following different paths, such as:
Installing Angular 6 by hand in a new project generated with npm init,
Installing and using the Angular CLI 6 to generate a new project (RECOMMENDED),
Upgrading from an existing Angular 5 project (Refer to sections on top for more information).

In this tutorial, we'll use the Angular CLI v6 to generate our Angular 6 front-end project. It's also the recommended way by the Angular team.
Requirements
This tutorial has a few requirements. Angular CLI depends on Node.js so you need to have Node and NPM - Node 8.9 or higher, together with NPM 5.5.1 - installed on your development machine. The easy way, is to go to their official website and get the appropriate installer for your operating system.
https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-16-04For Ubuntu 16.04 users I recommend following this tutorial to successfully install Node.js and NPM on your Ubuntu machine.
Now, just to make sure you have Node.js installed. Open a terminal and run the following command:
node -v
You should get the version of the installed Node.js 8.9+ platform.
Node version ~8.9+Installing Angular CLI 6
The Angular CLI is a powerful command line tool developed by the Angular team to generate Angular projects without the hassle of dealing with Webpack or complex configurations. It provides a fully-featured tool for working with your project from generating constructs such as components, pipes and services to serving and building production ready bundles etc.
To use the Angular CLI - you need to install it via npm - so go ahead and open your terminal and enter the following command:
npm install -g @angular/cli
Depending on your npm configuration, you may need to add sudo to install global packages.
A Primer on Angular CLI 6
After installing Angular CLI 6, you can run many commands. Let's start by checking the version of the installed CLI:
ng version
You should get a similar output:
Angular CLI version ~ ng versionA second command that you might need to run is the help command:
ng help
To get a complete usage help.
Angular CLI Usage ~ ng helpAngular CLI 6 - Generating a New Project
You can use Angular CLI 6 to quickly generate your Angular 6 project by running the following command in your terminal:
ng new frontend
frontend is the name of the project. You can - obviously- choose any valid name for your project. Since we'll create a full-stack application I'm using frontend as a name for the front-end application.
Angular CLI 6 - Serving your Project with a Development Server
Angular CLI provides complete tooling for developing on your local machine. As such, you don't need to install a local server to serve your project - you can simply, use the ng serve from your terminal to serve your project locally. So first navigate inside your project folder and run the following command:
cd frontend
ng serve
You can now navigate to http://localhost:4200/. The application will automatically live-reload if you change any of the source files.
You can also use different host address and port other than the default HTTP host and port by providing new options. For example:
ng serve --host 0.0.0.0 --port 8080
Agular CLI 6 - Generating Components, Directives, Pipes, Services and Modules
To bootstrap your productivity, Angular CLI provides a generate command to quickly generate basic Angular constructs such as components, directives, pipes, services and modules etc. For example to generate a component run:
ng generate component account-list
account-list is the name of the component. You can also use just g instead of generate
The Angular CLI will automatically add reference to components, directives and pipes in the app.module.ts.
If you want to add your component, directive or pipe to another module - other than the main application module i.e app.module.ts-for example to a feature module, you can simply prefix the name of the component with the module name and a slash - like a path.
ng g component account-module/account-list
account-module is the name of an existing module
Getting Started with Angular 6 - Introducing our CRM Application
Now, that we've generated a new Angular 6 project and seen the different Angular CLI commands to serve, build and work with our project. Let's use this knowledge to develop a front-end application for a RESTful back-end created with Python and Django - the well-know framework for perfectionists with deadlines. But first, let's get started by an introduction of what we are going to achieve.

[Original article](https://medium.com/techiediaries-com/angular-6-tutorial-series-jwt-auth-rxjs-6-httpclient-bootstrap-4-material-design-routing-and-f80f29ffcb6d)
