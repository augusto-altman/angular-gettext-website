---
title: 'Lazy-loading languages'
template: main.jade
---

# Lazy-loading languages

The default way of working with language strings is to [compile them to a JavaScript file and include them with your application](/dev-guide/compile/). This isn't feasible anymore once you have a lot of languages (or a lot of strings): the resulting JavaScript file would simply become too big.

There's another option: lazy-load the languages, only when you need them.

## Step 1: Compiling strings to JSON catalogues.
Instead of compiling to JavaScript (the default), configure your grunt task to output JSON files:

```javascript
grunt.initConfig({
    nggettext_compile: {
        all: {
            options: {
                format: "json"
            },
            files: [
                {
                    expand: true,
                    dot: true,
                    cwd: "po",
                    dest: "dist/languages",
                    src: ["*.po"],
                    ext: ".json"
                }
            ]
        },
    },
})
```

This will generate a `dist/languages/XX.json` file for each `po/XX.po`.

## Step 2: Load the languages in your application.
The gettextCatalog provides a `loadRemote` method to easily load new languages. Whenever you change the application languages, do something like this:

```javascript
angular.module("myApp").controller("helloController", function ($scope, gettextCatalog) {
    $scope.switchLanguage = function (lang) {
        gettextCatalog.setCurrentLanguage(lang);
        gettextCatalog.loadRemote("/languages/" + lang + ".json");
    };
});
```

All translations will be updated once the strings have been loaded.
