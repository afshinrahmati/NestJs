# NestJs

Nest (NestJS) is a framework for building efficient, scalable Node.js server-side applications. It uses progressive JavaScript, is built with and fully supports TypeScript (yet still enables developers to code in pure JavaScript) and combines elements of OOP (Object Oriented Programming), FP (Functional Programming), and FRP (Functional Reactive Programming).

Under the hood, Nest makes use of robust HTTP Server frameworks like Express (the default) and optionally can be configured to use Fastify as well!

Nest provides a level of abstraction above these common Node.js frameworks (Express/Fastify), but also exposes their APIs directly to the developer. This gives developers the freedom to use the myriad of third-party modules which are available for the underlying platform.

NestJS uses either Express or Fastify as the underlying HTTP server for handling requests and responses. By default, it’s built on top of Express, but you can switch to Fastify if you want better performance due to its optimized architecture.

Fastify is not implemented with Express. Fastify and Express are two separate frameworks that each provide their own approach to handling HTTP requests in Node.js. Here’s a breakdown of their differences and how they relate to NestJS:

1. Independent Frameworks
.Express and Fastify are both Node.js frameworks, but they are built independently with different goals in mind.
.Express is a minimalistic and flexible framework, widely known for its simplicity and large ecosystem. It’s one of the most popular frameworks for building Node.js applications.
.Fastify is designed to be lightweight and highly performant. It’s optimized for speed and low overhead, which is why it’s faster than Express in many benchmarks.


Express is well-suited for building a broader ecosystem, especially if you need to handle various types of requests (like HTML pages, templating, and different kinds of middleware). It’s also ideal if your application needs to integrate with a wide range of third-party tools and libraries. Express is excellent for building more traditional server-rendered web applications or full-featured web platforms.

Fastify shines when creating API-driven applications that focus on serving JSON responses, especially in microservices or high-performance APIs. It’s optimized for handling JSON data and can serve RESTful or GraphQL APIs efficiently, making it a strong choice for applications where API speed and scalability are critical. Fastify is particularly advantageous if your app is a backend for mobile apps, SPAs, or if you’re building a high-performance API.

for handleing nestjs hhtp we can use one of them.



# Key Features of NestJS:
## 1) Modular Architecture:
organizing code into modules, making it easier to structure large applications.
Each feature or functionality is typically encapsulated in its own module (e.g., UserModule, AuthModule). 
that this modular that the code will be code organization, reusability, and maintainability.
## 2) Dependency Injection (DI):
manage dependencies across the application.
* In object-oriented programming, every program contains several objects. These objects work together to do a series of tasks. So objects are interdependent. Before the concept of DI was introduced, an object was only responsible for providing the objects it had dependencies on, which caused problems. One of these problems was that the classes were strongly dependent on each other and it was difficult to separate them. It means that the classes are not independent from each other. As you can see, the objects are also dependent on each other :).
It was also difficult to test the program. Suppose we want to test class X, but this class depends on class Y. Y is a class that performs heavy operations. For example, a connection operation to a disk or an external service. Therefore, if the connection to the external service is not available, we cannot test the program!
**** WORNG ****
```
    class Car {
    public make() {
        const wheel = new PremiumWheel();
        const engine = new AdvancedEngine();
        // ...
    }
    }

    const premiumCar = new Car();
    premiumCar.make();
```    
**** concept ****
 With DI, the object itself is no longer responsible for providing its dependencies and dependencies are injected from outside. This injection is applied at Run Time. It means when the code is running.
```
   

    class Car {
    private wheel;
    private engine;

    public constructor(wheel: Wheel, engine: Engine) {
        this.wheel = wheel;
        this.engine = engine;
    }
}

```
1) Separation of Concerns 
With dependency injection, classes are doing their own work and are not aware of the implementation details of their dependencies.
2) Better Testability
## 3) TypeScript Support
## 4) Decorators:
Provides decorators for routes, controllers, and providers, enhancing readability and maintainability.
* Decorators are special functions that can be attached to classes, properties, methods, parameters, or accessors to add additional behavior. They enable you to "decorate" or modify a target element with extra functionality in a declarative way.
* In TypeScript, decorators are denoted with an @ symbol and are usually applied to classes, methods, or properties.
```
    function LogMethod(target: any, propertyKey: string, descriptor: PropertyDescriptor) {
    const originalMethod = descriptor.value;

    descriptor.value = function (...args: any[]) {
        console.log(`Calling ${propertyKey} with arguments:`, args);
        return originalMethod.apply(this, args);
    };

    return descriptor;
    }

    class Example {
    @LogMethod
    sayHello(name: string) {
        console.log(`Hello, ${name}!`);
    }
    }

    const example = new Example();
    example.sayHello("Afshin");
```
## 5) Extensible:  
Integrates well with other libraries and allows custom implementations.
## 6)Support Microservices :
Allows building microservices with built-in support for messaging protocols like gRPC, Redis, and MQTT ,RabbitMQ, Kafka .
Inter-Service Communication: It’s easy to build services that communicate with each other through message brokers or by using a REST API.
## 7)Extensive HTTP Layer:
* ### API:
connection between each services mostly we use API(application programming Interface) one of the typeof them is REstful Api , GraphQL
* #### ESTful API Support
REST==>Representational State Transfer) that is a structure for design system and it use Http PRotocol
in there each Resources accessable by url (Resources can be Data , service like html or json ,...).
each request has a url in restful api.
Cacheability,Representations(json,html,xml,..)
* ### Request Lifecycle
the Request Lifecycle refers to the series of steps a request undergoes from the moment it reaches a server to the point a response is sent back to the client. In frameworks like NestJS and Express, each stage of this lifecycle can be customized to handle tasks such as logging, validation, transformation, and security. Here’s a breakdown of the request lifecycle, specifically in NestJS, and how it compares to Express:
1) Incoming Request,
2) Middleware: are functions that execute before a route handler middleware can be used for tasks like authentication, logging, and parsing the request body.
3) Guards:act as authorization handlers, determining if a request should be allowed based on roles, permissions, or conditions.
4) Interceptors:  transform or manipulate data before sending it to the controller or returning a response to the client. Common uses are for data formatting and caching.Express: Doesn’t have built-in interceptors, so middleware is often used to handle data transformation.
5) Request Validation and Transformation with Pipes Pipes in NestJS can validate and transform incoming data before reaching the controller. Pipes are useful for data validation (e.g., checking that IDs are numbers) or transforming inputs to the correct format.
Express: You handle validation manually in each route or with libraries like express-validator
## 8) Graphql 
 a query language for APIs, instead of REST for managing and retrieving data. With GraphQL, developers can request only the data they need and receive exactly that,
 Resolvers and Queries: With decorators like @Resolver(), @Query(), and @Mutation(), developers can define GraphQL queries, mutations, and subscriptions seamlessly.
Subscription Support: Real-time features can be implemented via GraphQL subscriptions, making NestJS suitable for data-intensive applications needing real-time updates.
## 9) WebSocket and Real-Time Communication
WebSocket Integration: NestJS supports WebSocket for real-time communication, suitable for applications like chat systems, live notifications, and collaboration tools.
Pub/Sub Support: By combining WebSocket with a Pub/Sub model, you can handle complex event-driven patterns in real-time applications.
## 10) Asynchronous Programming and Performance
Async/Await: NestJS is built on top of asynchronous programming principles, making it well-suited for handling I/O-bound tasks and high-concurrency requirements.
## 11) Validation and Transformation with Pipes
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


# Export:
Sometimes, you might want to make certain providers or components of a module available for use in other modules.
# imports: 
In a Nest.js module, you import other modules, services, or dependencies that are required for the module to function properly.
# providers : 
things That Can Be used As Dependencies For Other Classes
Providers are typically services, repositories
# controller:
Controllers are responsible for handling incoming HTTP requests and returning appropriate responses.
nest g controller admin/campaign --flat<dont create an extra folder called controller>


# How to work Validation Pipe?
1) class-transformer => Turn the body into an instance of the DTO class.
2) class-validator => instance the validaton 
# step:
1) pipe: vlaidate Data in the request.
2) MessageController: Handle the request to a particular funcation
3) Service: 
*  it is a class and managing the business logic and this is repositories to find or store data.
4) Repository:
* it is a class to put storag<Access the data> the data in typeORM like Mongoose. comunicaton with hard disk.

# dependency injection:
const repo = new repo();
const service = new service(repo);
const contriller = new controlelr(service);
const repo = new repo();
const service = new service(repo);
const contriller = new controlelr(service);
const repo = new repo();
const service = new service(repo);
const contriller = new controlelr(service);
......
every momant we create a object and stack , heap ,....
## solve
* use dependency injection controlle the all create depeneced But no having to create a ton of different classes or instances.

# Nest DI Container:
* list od classes and their dependencies:
MessageService ==Depended==> MessageRepo.
*nest said so: list od instances that i have created :messageRepo, messagesService

# coupling <Loose & Tight>
 
In software development, "coupling" refers to the degree of interdependence between different components or modules in a system.
در توسعه نرم افزار، "coupling" به میزان وابستگی متقابل بین اجزا یا ماژول های مختلف در یک سیستم اشاره دارد.
Loose coupling means that components are relatively independent of each other, making them easier to change or replace without affecting the rest of the system.use with interface
اتصال شل به این معنی است که اجزاء نسبتاً مستقل از یکدیگر هستند و تغییر یا تعویض آنها را بدون تأثیر بر سایر قسمت های سیستم آسان تر می کن
Tight coupling, on the other hand, means that components are highly dependent on each other, making it difficult to modify or extend the system without impacting other parts.new Calass()
از سوی دیگر، اتصال محکم به این معنی است که اجزاء به شدت به یکدیگر وابسته هستند و تغییر یا گسترش سیستم را بدون تأثیرگذاری بر سایر قسمت‌ها دشوار می‌کند.

## Injectable
@Injectable(): This decorator is used to mark a class as a provider within the NestJS dependency injection system. Providers in NestJS are classes that can be injected into other classes or modules. When you mark a class with @Injectable(), NestJS knows that it can be instantiated by the dependency injection container and injected into other classes that depend on it. You typically use @Injectable() to define services, repositories, controllers, or other reusable components in your application.

Controllre use the Service so service is depened controller and app is start nest ask Controoler did you have depencedis Controoler said yes the Serivec and Serives is @Injectable so can Inject to an other class that need service instead of new (tight coupling) But first you defined me in module till nest realize I can be instance and controller and use me.
* if we use @Injectable() up the class that mean it becme looseCopuling and that mean if some class neeed it instanse it and use it very easily like a interface and any time we want we can use this instanse<depedncy>
forexample: we have service, and controller depenecd it first we come up the class service name we use @injectable and inject in module with provider or export and while app start nest check this controller and realize it has one depenced it name is service and in it looseCopuling so it instansed it on it when it need the service  and service do  like interface in Controller.
* if we use new in contollor for call class service any time  and it name is tight Copuling
const repo = new repo();
const service = new service(repo);
const contriller = new controlelr(service);
const repo = new repo();
const service = new service(repo);
const contriller = new controlelr(service);
const repo = new repo();
const service = new service(repo);
const contriller = new controlelr(service);
......
When you directly instantiate dependencies within a class (tight coupling) instead of using dependency injection (DI), it creates several issues:
1) Reduced Flexibility
2) Difficult Testing
3) Code Duplication
4) Harder to Refactor
5) Decreased Reusability

1) It promotes loose coupling by allowing classes to depend on abstractions rather than concrete implementations.
2) It makes your code more modular, testable, and maintainable by decoupling dependencies from their consumers.
3) It enables easy substitution of dependencies, making it simpler to change implementations or mock dependencies during testing.
4) It encourages better code organization and reuse by separating concerns and promoting a more modular architecture.


# @Inject
@Inject() tells Nest, "Hey, I know this says it is a Logger class, but really inject the provider with the injection token I tell you", which is useful for things like using specific instances of, say, a Logger class.
token for the path the type
# DI(Dependency Injection) Container Flow
* that is a design pattern 
1) startUp and Register all classs with Container.
2) Container figure out what each dependency class has.
3) automatically: then ask to Container for which class we create instance.
4) automatically: create all dependencies and give the class need the instance.
5) Contanier Hold this and reuse theme if needed.

# How Work DI <use loose coupling>:
In NestJS, dependency injection (DI) plays a crucial role in managing the components and their dependencies within your application. DI is a design pattern that promotes loose coupling by allowing components to depend on abstractions rather than concrete implementations. This makes your code more modular, testable, and easier to maintain.

Here's a more detailed overview of how dependency injection works in NestJS:

1. **Providers**: In NestJS, everything is a provider. Providers are classes annotated with the `@Injectable()` decorator. These classes can be services, controllers, repositories, or any other type of component that your application needs. Providers can inject dependencies via their constructors.

2. **Injection Tokens**: Each provider has an associated injection token. This token acts as a unique identifier for the provider and is used by the NestJS injector to resolve dependencies. Injection tokens are usually either the class name or a custom token defined using the `@Inject()` decorator.

3. **Constructor Injection**: Dependencies are injected into a class's constructor using TypeScript's constructor parameter syntax. When NestJS instantiates a class, it automatically resolves and injects the required dependencies based on their injection tokens.

4. **Module Configuration**: Dependency injection is primarily managed within NestJS modules. Modules are used to organize the components of your application and define the context in which dependencies are available. You can declare providers within a module using the `providers` property of the `@Module()` decorator.

5. **Module Imports and Exports**: Modules can import other modules, making their providers available for injection. This enables modularization and allows you to easily compose your application from smaller, reusable parts. You can also export providers from a module to make them available to other modules that import it.

6. **Scoping**: NestJS supports different scopes for providers, including singleton, transient, and request-scoped. Singleton providers are created once and shared across the entire application, transient providers are created each time they are injected, and request-scoped providers are created once per HTTP request.

7. **Custom Providers**: You can create custom providers by using the `@Injectable()` decorator to define a class and specifying its dependencies in the constructor. You can also use factories or value providers to customize the instantiation process further.

Overall, dependency injection in NestJS simplifies the management of dependencies, promotes code reusability, and enhances the testability and maintainability of your applications. By leveraging TypeScript's powerful type system and decorators, NestJS provides a robust foundation for building scalable and modular server-side applications.

1) Providers: annotated with @injectable controller and services and repositories
2) InjectionToken: each Provicer has unique token like nameClas Or custom token using @Inject
3) Constructos Injection: dependences are injected into any class want it.while a class need instandes it automatically injection the token.
4) Modules Configuration : first Injection do in Modules.you can management in their.
5) Modules can imports and export


 <!-- imports:[PowerModule],// in there list of dependensis is CpuService + PowerService + all thing in PowerModule -->


 # Mongo:
1) The forRoot(): method accepts the same configuration object as mongoose.connect() from the Mongoose package, as described here.
2) The @Schema() decorator marks a class as a schema definition.
3) The @Prop() decorator defines a property in the document. 

# Redis:
install: cache-manager + cache-manager-redis-store



Feature            | NestJS                                         | Express
-------------------|-----------------------------------------------|-----------------------------------------
Architecture       | MVC with modules, dependency injection, decorators | Minimal and unopinionated
TypeScript         | TypeScript-first with type safety             | Primarily JavaScript, TypeScript with configuration
Learning Curve     | Higher due to advanced abstractions and TypeScript requirement | Lower, simpler to start
Flexibility        | Structured and opinionated; ideal for large apps | Flexible, suitable for smaller, quick setups
Built-In Features  | Dependency injection, testing utilities, interceptors, guards | Minimal features, extend with middleware
Scalability        | Modular and highly scalable                   | Can be scalable, but requires more custom setup
Performance        | Slightly less performant due to abstraction layers | Lightweight and fast
Use Case           | Ideal for large, complex, maintainable apps  | Suitable for lightweight APIs, MVPs



Here’s a breakdown of the differences between **Fastify**, **Express**, and **NestJS**, considering their design philosophies, features, performance, and use cases:

---

### **1. Fastify**
#### **Overview**  
Fastify is a fast and low-overhead web framework for Node.js that focuses on performance and developer experience. It uses an asynchronous programming model with Promises and provides schema-based validation.

#### **Key Features**
- **Performance:** Highly optimized for speed; significantly faster than Express.
- **Schema Validation:** Built-in support for request/response validation using JSON Schema.
- **Plugin System:** Modular and extensible plugin system.
- **Asynchronous Handling:** Fully asynchronous with native `async/await` support.
- **Lightweight:** Minimalist design with less overhead.

#### **When to Use Fastify**
- You need high-performance APIs.
- You're building microservices or APIs with strict validation requirements.
- You prefer minimal abstractions and flexibility over structured frameworks.

---

### **2. Express.js**
#### **Overview**  
Express.js is a minimalist and unopinionated web framework for Node.js. It has been the de-facto standard for building web applications and APIs for years.

#### **Key Features**
- **Unopinionated:** Gives you the freedom to structure your application as you see fit.
- **Middleware-Based:** Relies heavily on middleware for request/response handling.
- **Ecosystem:** Large ecosystem of third-party packages.
- **Simplicity:** Easy to learn and use, with minimal boilerplate.

#### **When to Use Express.js**
- You want a flexible framework to build both small and large web applications.
- You don’t need strict patterns or structures.
- You want access to a large community and ecosystem of middleware.

---

### **3. NestJS**
#### **Overview**  
NestJS is a progressive, opinionated framework for building scalable and maintainable server-side applications. It is built on top of Express (or optionally Fastify) and leverages TypeScript by default.

#### **Key Features**
- **Opinionated:** Follows architectural patterns like **MVC** and **Dependency Injection**.
- **Scalable:** Designed for large-scale applications with modularity in mind.
- **Decorator-Based Syntax:** Uses decorators for defining routes, services, controllers, and more.
- **Built-In Tools:** Comes with built-in support for WebSockets, GraphQL, microservices, testing, etc.
- **Express/Fastify Underlying:** Allows you to choose between Express and Fastify as the HTTP server.
- **TypeScript First:** Encourages the use of TypeScript, but also supports JavaScript.

#### **When to Use NestJS**
- You are building large-scale, enterprise-grade applications.
- You want a structured and maintainable architecture.
- You need features like dependency injection, modularity, and integrated support for advanced tools like GraphQL, WebSockets, or microservices.

---

### **Comparison Table**

| **Feature**                  | **Fastify**                     | **Express.js**                 | **NestJS**                          |
|-------------------------------|----------------------------------|---------------------------------|--------------------------------------|
| **Performance**              | 🚀 Extremely Fast               | 🐢 Moderate                    | Depends on Fastify/Express backend |
| **Learning Curve**           | 📈 Moderate                     | 📉 Easy                        | 📈 Steeper (due to structure)       |
| **Extensibility**            | ✅ Plugin System                | ✅ Middleware                  | ✅ Modular with DI                  |
| **TypeScript Support**       | ✅ Good                         | 🟡 Basic (via @types)          | ✅ Excellent (default)              |
| **Architecture**             | Unopinionated                   | Unopinionated                  | Opinionated (MVC/DI)                |
| **Validation**               | ✅ Built-in JSON Schema         | ❌ Manual (or 3rd-party)       | ✅ Built-in                         |
| **Best Use Case**            | High-performance APIs           | General-purpose web apps/APIs  | Scalable enterprise applications    |
| **Underlying HTTP Engine**   | Custom                          | Node.js HTTP module            | Express or Fastify                  |
| **Community Support**        | Growing                         | Very Large                     | Growing Fast                        |
| **Built-In Tools**           | ❌ Minimal                      | ❌ Minimal                     | ✅ Rich (e.g., GraphQL, WebSockets) |

---

### **Key Takeaways**

- **Use Fastify** if performance is your top priority, and you want a lightweight, schema-based validation framework for building APIs.
- **Use Express.js** if you want a simple, flexible, and community-supported framework for both small and medium-sized projects.
- **Use NestJS** if you need a robust, opinionated framework for large-scale, maintainable applications with modern features like DI, modularity, and TypeScript integration.

Let me know if you'd like more details or examples for any of these frameworks! 🚀