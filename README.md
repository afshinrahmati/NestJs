# NestJs

Nest (NestJS) is a framework for building efficient, scalable Node.js server-side applications. It uses progressive JavaScript, is built with and fully supports TypeScript (yet still enables developers to code in pure JavaScript) and combines elements of OOP (Object Oriented Programming), FP (Functional Programming), and FRP (Functional Reactive Programming).

Under the hood, Nest makes use of robust HTTP Server frameworks like Express (the default) and optionally can be configured to use Fastify as well!

Nest provides a level of abstraction above these common Node.js frameworks (Express/Fastify), but also exposes their APIs directly to the developer. This gives developers the freedom to use the myriad of third-party modules which are available for the underlying platform.
# what is nest CLI ?
1) Tool for generating + running project

# nestjs library:
* Common: contains majority of functions,class,etc that we need from Nest.
* platform-express : let to the nest js use express.js for handling HTTP request.
* reflect-metadata: helps for make decorators work.
# nestjs server:
* handling Request and Response on Http implementation can use Express.js or Fastify.
default is Express.
# Nestjs
1) npm i -g @nestjs/cli the nest new  OR yarn add @nestjs/common @nestjs/core @nestjs/platform-express reflect-metadata typescript
2) nest new 

# path on server
> [!Pipe]
> validate Data.

> [!Guard]
> make sure about user authenticated.

> [!Controller]
> Routes Handles incoming Request.

> [!Service]
> Run and Handles some business Logic.
 
> [!Module]
> Groups together code.

> [!Filters]
> Handles Error from Request Handling.

> [!Interceptors]
> Add extra logic to incoming Request or out going the Response

> [!Repository]
> Access to on Databases.


### @controller():
Use `controller` for Routing and it is decorator

# what is decorator ?
In programming, a decorator is a design pattern that allows behavior
to be added to individual objects or classes dynamically,
without affecting the behavior of other objects from 
the same class. Decorators are typically used to modify or extend the 
behavior of functions or methods at runtime. like order hotel like with breakfast or dinner or wifi

type ClassDecorator = <TFunction extends Function>(target: TFunction) => TFunction | void;