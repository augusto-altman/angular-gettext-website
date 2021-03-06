---
title: 'Installing'
template: main.jade
---

# Adding angular-gettext to your project

**Step 1:** Grab the files, either by copying the files from the `dist` folder or (preferably) through bower or npm:

```
bower install --save angular-gettext
```

or

```
npm install --save angular-gettext
```


**Step 2:** Include the angular-gettext source files in your app:

```xml
<script src="bower_components/angular-gettext/dist/angular-gettext.min.js"></script>
```

or

```xml
<script src="node_modules/angular-gettext/dist/angular-gettext.min.js"></script>
```

**Step 3:** Add a dependency to angular-gettext in your Angular app:

```javascript
angular.module('myApp', ['gettext']);
```

You can now start using the `translate` directive to mark strings as translatable.

<a href="/dev-guide/annotate/" class="btn btn-primary">Next: Annotate strings</a>
