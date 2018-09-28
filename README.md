# C# to TypeScript

*NOTE!* This is a fork of [jonathanp/csharp-models-to-typescript](https://github.com/jonathanp/csharp-models-to-typescript). If you do not need to convert methods you should use the original one instead.

## Changes from original

1. I added the option `methods` (boolean, default false). Set to true to convert methods.
2. I added the option `returnPromise`. Set to true to make interface methods return promises.
3. Create separate npm package (csharp-to-typescript). I removed `model` from the name as methods may not be seen as part of a data model.

## Versions

- V1.0.0 - fork of version 0.0.8

# C# models to TypeScript

This is a tool that consumes your C# domain models and types and creates TypeScript declaration files from them. There's other tools that does this but what makes this one different is that it internally uses [Roslyn (the .NET compiler platform)](https://github.com/dotnet/roslyn) to parse the source files, which removes the need to create and maintain our own parser.

## Dependencies

* [.NET Core SDK](https://www.microsoft.com/net/download/macos)

## Install

```
$ npm install --save dlid-csharp-models-to-typescript
```

## How to use

1. Add a config file to your project that contains for example...

```
{
    "include": [
        "./models/**/*.cs",
        "./enums/**/*.cs"
    ],
    "exclude": [
        "./models/foo/bar.cs"
    ],
    "namespace": "Api",
    "output": "./api.d.ts",
    "camelCase": false,
    "methods": true,
    "returnPromise": true,
    "stringLiteralTypesInsteadOfEnums": false,
    "customTypeTranslations": {
        "ProductName": "string",
        "ProductNumber": "string"
    }
}
```

2. Add a npm script to your package.json that references your config file...

```
"scripts": {
    "generate-types": "csharp-models-to-typescript --config=your-config-file.json"
},
```

3. Run the npm script `generate-types` and the output file specified in your config should be created and populated with your models.


## License

MIT © [Jonathan Persson](https://github.com/jonathanp)
Fork with method support maintained by [David Lidström](https://github.com/dlid)
