### nestjs/swagger-cli bug report

how to reproduce bug

1. `npm install`
2. delete `dist` folder if exists.
3. remove `@nestjs/swagger` in `compilerOptions.plugins` array in `nest-cli.json`
now your nest-cli.json look like this
```json
{
  "collection": "@nestjs/schematics",
  "sourceRoot": "src",
  "compilerOptions": {
    "plugins": []
  }
}
```
4. run `npm run start:dev` to build & run dev server.
5. ctrl+c and turn off your dev server.
6. add `@nestjs/swagger` in `compilerOptions.plugins` array in `nest-cli.json`
now your nest-cli.json look like this
```json
{
  "collection": "@nestjs/schematics",
  "sourceRoot": "src",
  "compilerOptions": {
    "plugins": ["@nestjs/swagger"]
  }
}
```

now, swagger-cli plugin is installed, so it should work but it doesn't.
even when code change triggers re-compile, it still doesn't update API document.
you have to **manually delete** `dist` folder to fix that.