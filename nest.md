1. **What is Nest.js?**
   - **Answer:** Nest.js is a progressive Node.js framework for building efficient, scalable, and maintainable server-side applications. It combines elements of Object-Oriented Programming, Functional Programming, and Reactive Programming.

2. **Explain the concept of Dependency Injection in Nest.js.**
   - **Answer:** Dependency Injection is a design pattern in which the framework injects dependencies into a class, making components more modular and testable. Example:

      ```typescript
      // Service with dependency injected
      @Injectable()
      export class UserService {
        constructor(private readonly userRepository: UserRepository) {}

        // Service methods using userRepository
      }
      ```

3. **What is the purpose of Decorators in Nest.js?**
   - **Answer:** Decorators are used to enhance or modify classes and their properties in Nest.js. They provide metadata and allow the framework to understand the structure of the application. Example:

      ```typescript
      // Controller with decorator
      @Controller('users')
      export class UsersController {
        // Controller methods
      }
      ```

4. **Explain the concept of Middleware in Nest.js.**
   - **Answer:** Middleware in Nest.js is a function that has access to the request, response, and next function. It can modify the request or response, terminate the request-response cycle, or call the next middleware. Example:

      ```typescript
      // Middleware example
      export function loggerMiddleware(req, res, next) {
        console.log(`Request: ${req.method} ${req.path}`);
        next();
      }
      ```

5. **What is the Nest.js module system?**
   - **Answer:** The Nest.js module system is a way of organizing components and services into cohesive and reusable units. It helps in structuring the application and managing dependencies.

      ```typescript
      // Module example
      @Module({
        controllers: [UsersController],
        providers: [UserService],
      })
      export class UsersModule {}
      ```

6. **Explain the concept of Pipes in Nest.js.**
   - **Answer:** Pipes in Nest.js are used for data transformation or validation. They can modify input data before it reaches the route handler. Example:

      ```typescript
      // Pipe example
      export class ValidationPipe implements PipeTransform {
        transform(value: any, metadata: ArgumentMetadata) {
          // Transform or validate data
          return value;
        }
      }
      ```

7. **What is the purpose of Guards in Nest.js?**
   - **Answer:** Guards are used to control access to routes or methods based on certain conditions. They can be used for authentication, authorization, and input validation. Example:

      ```typescript
      // Guard example
      @Injectable()
      export class AuthGuard implements CanActivate {
        canActivate(context: ExecutionContext): boolean | Promise<boolean> | Observable<boolean> {
          // Check authentication
          return true;
        }
      }
      ```

8. **Explain the use of Interceptors in Nest.js.**
   - **Answer:** Interceptors in Nest.js are used to intercept and modify the response object before it is sent to the client. They provide a way to globally process responses. Example:

      ```typescript
      // Interceptor example
      @Injectable()
      export class LoggingInterceptor implements NestInterceptor {
        intercept(context: ExecutionContext, next: CallHandler): Observable<any> {
          console.log('Before...');
          return next.handle().pipe(tap(() => console.log('After...')));
        }
      }
      ```

9. **What is DTO (Data Transfer Object) in Nest.js?**
   - **Answer:** DTOs are objects that define how data is sent over the network between different parts of the application. They help in validating and shaping incoming data. Example:

      ```typescript
      // DTO example
      export class CreateUserDto {
        @IsString()
        readonly username: string;

        @IsEmail()
        readonly email: string;
      }
      ```

10. **Explain the use of Swagger in Nest.js.**
    - **Answer:** Swagger is used in Nest.js to generate interactive API documentation. It allows developers to explore and test API endpoints easily. Example:

        ```typescript
        // Swagger example
        const config = new DocumentBuilder()
          .setTitle('Nest.js API')
          .setDescription('API documentation for Nest.js app')
          .setVersion('1.0')
          .addTag('users')
          .build();

        const document = SwaggerModule.createDocument(app, config);
        SwaggerModule.setup('api', app, document);
        ```

11. **How does Nest.js handle CORS (Cross-Origin Resource Sharing)?**
    - **Answer:** Nest.js can handle CORS by using the `CorsMiddleware`. It can be configured to allow or restrict cross-origin requests. Example:

        ```typescript
        // CORS configuration
        const app = await NestFactory.create(AppModule);
        app.enableCors({
          origin: 'http://example.com',
          methods: 'GET,HEAD,PUT,PATCH,POST,DELETE',
          credentials: true,
        });
        ```

12. **What is the purpose of the `@nestjs/graphql` module in Nest.js?**
    - **Answer:** The `@nestjs/graphql` module allows developers to build GraphQL APIs in Nest.js. It integrates with the Apollo Server and provides decorators for defining GraphQL schemas, resolvers, and directives.

      ```typescript
      // GraphQL schema example
      @ObjectType()
      class User {
        @Field()
        username: string;
      }

      @Resolver(() => User)
      class UserResolver {
        @Query(() => User)
        getUser() {
          // Resolver logic
          return { username: 'john_doe' };
        }
      }
      ```

These questions cover various aspects of Nest.js, from basic concepts like decorators to advanced topics like interceptors and GraphQL integration. Understanding these concepts will help you in Nest.js interviews.
