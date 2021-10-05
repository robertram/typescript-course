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
