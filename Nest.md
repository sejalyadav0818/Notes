 basic User CRUD operation 

### Step 1: Create User DTO (Data Transfer Object)

Create a `user.dto.ts` file in the `user` module folder to define the structure of the data being transferred:

```typescript
// src/user/dto/user.dto.ts

export class CreateUserDto {
  readonly name: string;
  readonly email: string;
  readonly password: string;
}

export class UpdateUserDto {
  readonly name?: string;
  readonly email?: string;
  readonly password?: string;
}
```

### Step 2: Create User Entity

In the `user` module, create a `user.entity.ts` file to define the User entity:

```typescript
// src/user/user.entity.ts

import { Prop, Schema, SchemaFactory } from '@nestjs/mongoose';
import { Document } from 'mongoose';

@Schema({ timestamps: true })
export class User extends Document {
  @Prop({ required: true })
  name: string;

  @Prop({ required: true })
  email: string;

  @Prop({ required: true })
  password: string;
}

export const UserSchema = SchemaFactory.createForClass(User);
```

### Step 3: Create User Service

Create a `user.service.ts` file in the `user` module folder for the User service:

```typescript
// src/user/user.service.ts

import { Injectable, NotFoundException } from '@nestjs/common';
import { Model } from 'mongoose';
import { InjectModel } from '@nestjs/mongoose';
import { User } from './user.entity';
import { CreateUserDto, UpdateUserDto } from './dto/user.dto';

@Injectable()
export class UserService {
  constructor(@InjectModel(User.name) private readonly userModel: Model<User>) {}

  async create(createUserDto: CreateUserDto): Promise<User> {
    const createdUser = new this.userModel(createUserDto);
    return createdUser.save();
  }

  async findAll(): Promise<User[]> {
    return this.userModel.find().exec();
  }

  async findById(id: string): Promise<User | null> {
    return this.userModel.findById(id).exec();
  }

  async update(id: string, updateUserDto: UpdateUserDto): Promise<User | null> {
    const result = await this.userModel.findByIdAndUpdate(id, updateUserDto, { new: true }).exec();
    return result ? (result as User) : null;
  }

  async delete(id: string): Promise<void> {
    const result = await this.userModel.findByIdAndDelete(id).exec();
    if (!result) {
      throw new NotFoundException('User not found');
    }
  }
}
```

### Step 4: Create User Controller

Create a `user.controller.ts` file in the `user` module folder for the User controller:

```typescript
// src/user/user.controller.ts

import { Controller, Get, Post, Body, Param, Patch, Delete } from '@nestjs/common';
import { UserService } from './user.service';
import { User } from './user.entity';
import { CreateUserDto, UpdateUserDto } from './dto/user.dto';

@Controller('users')
export class UserController {
  constructor(private readonly userService: UserService) {}

  @Post()
  async create(@Body() createUserDto: CreateUserDto): Promise<User> {
    return this.userService.create(createUserDto);
  }

  @Get()
  async findAll(): Promise<User[]> {
    return this.userService.findAll();
  }

  @Get(':id')
  async findById(@Param('id') id: string): Promise<User | null> {
    return this.userService.findById(id);
  }

  @Patch(':id')
  async update(@Param('id') id: string, @Body() updateUserDto: UpdateUserDto): Promise<User | null> {
    return this.userService.update(id, updateUserDto);
  }

  @Delete(':id')
  async delete(@Param('id') id: string): Promise<void> {
    return this.userService.delete(id);
  }
}
```

### Step 5: Register Module and Controller

In the `user.module.ts` file, register the module and the controller:

```typescript
// src/user/user.module.ts

import { Module } from '@nestjs/common';
import { MongooseModule } from '@nestjs/mongoose';
import { UserController } from './user.controller';
import { UserService } from './user.service';
import { User, UserSchema } from './user.entity';

@Module({
  imports: [
    MongooseModule.forFeature([{ name: User.name, schema: UserSchema }]),
  ],
  controllers: [UserController],
  providers: [UserService],
})
export class UserModule {}
```

### Step 6: Register User Module in AppModule

Finally, in your `app.module.ts`, make sure to register the `UserModule`:

```typescript
// src/app.module.ts

import { Module } from '@nestjs/common';
import { MongooseModule } from '@nestjs/mongoose';
import { UserModule } from './user/user.module';

@Module({
  imports: [
    MongooseModule.forRootAsync({
      useFactory: () => ({
        uri: process.env.MONGODB_URI,
        useNewUrlParser: true,
        useUnifiedTopology: true,
      }),
    }),
    UserModule,
  ],
  controllers: [],


  providers: [],
})
export class AppModule {}
```

# Test CRUD API's with Swagger 

1. **Ensure Swagger Module is Installed:**
   Make sure you have the `@nestjs/swagger` package installed. If not, you can install it using:

   ```bash
   npm install --save @nestjs/swagger swagger-ui-express
   ```

2. **Set up Swagger Configuration:**
   In your Nest.js application, you need to configure the Swagger module. Create a file, let's call it `swagger.config.ts`, and define your Swagger configuration:

   ```typescript
   import { DocumentBuilder, SwaggerModule } from '@nestjs/swagger';

   export const setupSwagger = (app) => {
     const config = new DocumentBuilder()
       .setTitle('Your API Title')
       .setDescription('Your API Description')
       .setVersion('1.0')
       .build();

     const document = SwaggerModule.createDocument(app, config);
     SwaggerModule.setup('api', app, document);
   };
   ```

3. **Apply Swagger Configuration in AppModule:**
   In your `AppModule` or a dedicated module, import the `setupSwagger` function and call it to set up Swagger:

   ```typescript
   import { Module } from '@nestjs/common';
   import { MongooseModule } from '@nestjs/mongoose';
   import { setupSwagger } from './swagger.config'; // Import the setupSwagger function
   import { UserModule } from './user/user.module';

   @Module({
     imports: [
       MongooseModule.forRoot('mongodb://localhost/user-crud-app', { autoCreate: true }),
       UserModule,
     ],
     controllers: [],
     providers: [],
   })
   export class AppModule {
     // Call setupSwagger in the constructor
     constructor() {
       setupSwagger(this);
     }
   }
   ```

4. **Decorate Your Controllers with Swagger Decorators:**
   In your controllers (e.g., `user.controller.ts`), use Swagger decorators to provide additional information about your API:

   ```typescript
   import { Controller, Get, Post, Body } from '@nestjs/common';
   import { ApiResponse, ApiTags } from '@nestjs/swagger';
   import { CreateUserDto } from './dto/create-user.dto';
   import { UserService } from './user.service';

   @Controller('users')
   @ApiTags('users') // Optional: Add tags for Swagger documentation
   export class UserController {
     constructor(private readonly userService: UserService) {}

     @Get()
     @ApiResponse({ status: 200, description: 'List of users' })
     findAll() {
       return this.userService.findAll();
     }

     @Post()
     @ApiResponse({ status: 201, description: 'User has been successfully created.' })
     create(@Body() createUserDto: CreateUserDto) {
       return this.userService.create(createUserDto);
     }
   }
   ```

5. **Run Your Application:**
   Start your Nest.js application. If you've set up everything correctly, you should be able to access Swagger UI at `http://localhost:3000/api`. Adjust the URL based on your application's configuration.






