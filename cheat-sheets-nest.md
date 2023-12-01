# Cheat sheets Nest

## Init nest :
  
Créer un porjet avec Nest :  
`npm i -g @nestjs/cli`  
`$ nest new project-name`  
  
Installer le Package manager :  
`pnpm install`  
  
Running the app :  
*development*  
`pnpm run start`  
*watch mode*  
`pnpm run start:dev`  
*production mode*  
`pnpm run start:prod`  
  
test :  
*unit tests*  
`pnpm run test`  
*e2e tests*  
`pnpm run test:e2e`  
*test coverage*  
`pnpm run test:cov`  
  
Créer une route :
- dans controller.ts 
```bash
import { Controller, Get } from '@nestjs/common';
import { AppService } from './app.service';

@Controller()
export class AppController {
  constructor(private readonly appService: AppService) {}

  @Get()
  getHello(): string {
    return this.appService.getHello();
  }
  #ici nouvelle route sayGoobye
   @Get()
   sayGoodbye(): string {
    return this.appService.sayGoodbye();
   }
}
```
- dans service.ts  
```bash
import { Injectable } from '@nestjs/common';

@Injectable()
export class AppService {
  getHello(): string {
    return 'Hello World!';
  }
  # Nouvelle route
  sayGoodbye(): string {
    return 'Goodbye';
  }
}
```

Nouveau dossier :  
Changer les Variables et export + import les modules entre eux. 
  
le string :  
`nomDeFonction(): string {...}`
*la fonction est obligé de renvoyer une chaîne de caractère*  
`nomDeFonction(): string[] {...}`
*La fonction est obligé de renvoyer une table*  
  
Installer une dépendance/package  
`pnpm install prisma --save-dev`  
  
Vérifier le env.  
`DB_URL="postgresql://thibaud:Payen@localhost:5432/projetNest"`  
  
Vérifier le schema.prisma, il doit contenir les tables et les liens logique
```bash
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DB_URL")
}
# puis les table
```
