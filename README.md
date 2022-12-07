# To Reproduce error

From repo root:

- `npm install`
- `dotnet tool restore`
- `dotnet paket install`
- `npm start` or `dotnet fable src --noCache`

The error output:

```
> dotnet fable src --noCache
Fable: F# to JS compiler 3.7.20
Thanks to the contributor! @Neftedollar
Stand with Ukraine! https://standwithukraine.com.ua/

Parsing src\App.fsproj...
src> cmd /C dotnet restore App.fsproj -p:FABLE_COMPILER=true
  Determining projects to restore...
  Paket version 7.2.0+bb14ab674b2748070a624f394cd6796e11aaffa8
  The last full restore is still up to date. Nothing left to do.
  Total time taken: 0 milliseconds
  Paket version 7.2.0+bb14ab674b2748070a624f394cd6796e11aaffa8
  Restoring C:\Repos\minimal-fable\src\App.fsproj
  Starting restore process.
  Total time taken: 0 milliseconds
  Restored C:\Repos\minimal-fable\src\App.fsproj (in 257 ms).
Project and references (1 source files) parsed in 7401ms

Started Fable compilation...
Fable compilation finished in 1993ms

.\src\App.fs(5,6): (5,13) error FSHARP: The namespace or module 'Browser' is not defined. (code 39)
.\src\App.fs(11,16): (11,24) error FSHARP: The value, namespace, type or module 'document' is not defined. (code 39)
.\src\App.fs(11,57): (11,64) error FSHARP: The namespace or module 'Browser' is not defined. (code 39)
.\src\App.fs(14,1): (14,17) error FSHARP: Lookup on object of indeterminate type based on information prior to this program point. A type annotation may be needed prior to this program point to constrain the type of the object. This may allow the lookup to be resolved. (code 72)
Compilation failed
```

# Fable Minimal App

This is a small Fable app project so you can easily get started and add your own code progressively. For more comprehensive templates [check this page](https://fable.io/docs/2-steps/your-first-fable-project.html).

## Requirements

* [dotnet SDK](https://www.microsoft.com/net/download/core) 5.0 or higher
* [node.js](https://nodejs.org)
* An F# editor like Visual Studio, Visual Studio Code with [Ionide](http://ionide.io/) or [JetBrains Rider](https://www.jetbrains.com/rider/)

## Building and running the app

* Install dependencies: `npm install`
* Start the compiler in watch mode and a development server: `npm start`
* After the first compilation is finished, in your browser open: http://localhost:8080/

Any modification you do to the F# code will be reflected in the web page after saving.

> Note: check the "scripts" section in `package.json` to see the commands triggered by the steps above.

## Bundling for release

Run the following command to compile and bundle up all your F# code into one Javascript file: `npm run build`. The compiled output ends up in the `public` folder under the name `bundle.js`.

## Project structure

### npm

JS dependencies are declared in `package.json`, while `package-lock.json` is a lock file automatically generated.

### Webpack

[Webpack](https://webpack.js.org) is a JS bundler with extensions, like a static dev server that enables hot reloading on code changes. Configuration for Webpack is defined in the `webpack.config.js` file. Note this sample only includes basic Webpack configuration for development mode, if you want to see a more comprehensive configuration check the [Fable webpack-config-template](https://github.com/fable-compiler/webpack-config-template/blob/master/webpack.config.js).

### F#

The sample only contains two F# files: the project (.fsproj) and a source file (.fs) in the `src` folder.

### Web assets

The `index.html` file and other assets like an icon can be found in the `public` folder.
