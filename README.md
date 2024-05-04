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