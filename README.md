# typescript-course

## Commands

| Command             | Description                              |
| :------------------ | :--------------------------------------- |
| `tsc`               | Compile ts file into js                  |
| `tsc --outDir dist` | Compile ts file into js in a dist folder |
| `tsc --outDir dist --watch` | Listens to the files changes and compiles them into de dist folder |

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


