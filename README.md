# typescript-course

## Commands

| Command             | Description                              |
| :------------------ | :--------------------------------------- |
| `tsc`               | Compile ts file into js                  |
| `tsc --outDir dist` | Compile ts file into js in a dist folder |
| `tsc --outDir dist --watch` | Listens to the files changes and compiles them into de dist folder |
| `tsc && node/dist` | Compiles and then run the index.js in the compiled directory |

## Modules and targets

[Typescript modules docs](https://www.typescriptlang.org/docs/handbook/2/modules.html)


```bash
  tsc --module es2020 --taget es2020 --outDir dist/es2020
```

Compiles with the es2020 module 

```bash
tsc --module amd --target es2020 --outDir dist/amd
```

Compiles with the amd module


## Webpack 

[Webpack basic setup](https://webpack.js.org/guides/getting-started/#basic-setup)

```bash
npm install webpack webpack-cli --save-dev
```

[Webpack with typescript setup](https://webpack.js.org/guides/getting-started/#basic-setup)


```bash
npm install --save-dev typescript ts-loader
```

Node that it includes ts-loader

### Webpack script in package.json

Include the build script. 

```bash
 "scripts": {
    "build": "webpack"
  },
```

### Webpack config

[Create webpack config easier](https://createapp.dev/)

```bash
 entry: './src/main.ts',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js',
  },
```

The output for the webpack compilation in this case will be in dist/bundle.js
Now we create and index.html and include the bundle file in a script in the head


### Http-server

[Npm library](https://www.npmjs.com/package/http-server)

This library allows us to execute a local server 

With the library installed we can run this command and see the compiled results of our code in the browser

```bash
 http-server ./dist/ -d false
```

## Typescript Tricks

### Alias

These are examples of alias you can use to either replace the real name or to give a name of something you are exporting 

```bash
import * as content from '../assets/content.json';
import { ComplicatedJoke as HardJoke, Joke, Quote, Riddle } from '@yfx/models';
```

### Barrel files

It is a file that recolects interfaces, types, functions, etc. You can create it by naming it index.ts inside a directory. And the content could look like:

```bash
export * from './common.types';
export * from './joke.interface';
export * from './quote.interface';
export * from './riddle.interface';
```

That way you can call the files like this

```bash
import { Qoute, Joke } from './interfaces'
```

Instead of 

```bash
import { Quote } from './interfaces/quote.interface';
import { Riddle } from './interfaces/riddle.interface';
```

### Relative Routes

You can add paths to the typescript config so you can access routes relatives to the paths added


```bash
    "baseUrl": "./src",
    "paths": {
      "models": ["interfaces/index.ts"]
    }
```

This way you can import it like

```bash
  import { Joke, Quote, Riddle } from 'models';
```


### Consume Json files

You need to add this config to the tsconfig.json to be able to read json files in the project  

```bash
"resolveJsonModule": true,
```


### Libraries with no types

If you install a library that was built on javascript and doesnt have types, typescript gives us this site to look for the types for that library

[Typescript Search](https://www.typescriptlang.org/dt/search?search=)


Example: 
```bash
npm i lodash
npm i @types/lodash --save-dev
```


### Types declaration in the library

To declare all the types files in the distribution folder you can add this to the tsconfig

```bash
"declaration": true,
```

Then when you run the build, it will create a types file for each javascript file
For example: 
- joke.interface.js -> joke.interface.d.ts

Also if you include this config, the types files will be created in the dist/types folder

```bash
"declarationDir": "dist/types"
```

## Publish library to npm

### Package.json config

You need to add this config so that the package manager recognizes where to find the javascript file and the types file

```bash
 "main": "dist/main.js",
 "types": "dist/types/main.d.ts",
```

### Package.json scripts

Also these are the scripts you will need so that npm can build the library

```bash
 "scripts": {
    "prepublish": "npm run build",
    "build": "tsc"
  },
```

### Semantic Versioning

[Semver](https://semver.org/)

In this website you can find an explanation of how you can use the versioning in the library. But in summary:
   - MAJOR version when you make incompatible API changes,
   - MINOR version when you add functionality in a backwards compatible manner, and
   - PATCH version when you make backwards compatible bug fixes.

### Publish

To publish the library you have to run 

```bash
 npm login
```
```bash
 npm publish
```

### Init modules

You can import init.ts files for example if you need to initialize a variable in that file before running your code

```bash
 import './init'
```









