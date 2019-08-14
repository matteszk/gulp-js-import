Forked version of https://github.com/nambo/gulp-js-import, adds more options.

## INSTALL

```
npm install gulp-js-import-file --save-dev
```
## USAGE

First, install `gulp-js-import-file` as a devDependency:

Then add it to the gulpfile.js:


```
var gulp = require('gulp');
var jsImport = require('gulp-js-import-file');

gulp.task('import', function() {
  return gulp.src('index.js')
        .pipe(jsImport({
            hideConsole: true,
            importStack: true
        }))
        .pipe(gulp.dest('dist'));
});
```

Final, run import task where you need, eg: `gulp import`

## DEMO

you can get all code [here](https://github.com/newlogic-cz/gulp-js-import-file)

### File Tree

this is the file tree:

```
demo
|
-- widget
|   |
|   -- widget.js
|   |
|   -- config.js
|   
-- index.js
|   
-- gulpfile.js
|   
-- package.json
```
### Brief Intorduce
index.js:


```
// index.js

@import './widget/widget.js'

output(config);

// index.js end
```

in `index.js`, you can use `@import 'xxx.js'` when you want import a js file

### Options
* hideConsole - hides console
* importStack - import file only once
* es6import - you don't have to use @ as prefix

### Run

Enter the `demo` directory in command

```
cd demo
```
Install `gulp` `gulp-js-import-file` 

```
gulp install
```
Compile files

```
gulp import
```
You could see a js file `dist/index.js` like this:

```
// index.js
// widget.js
// config.js
var config = 'this is config value';
// config.js end

function output(str) {
  console.log(str);
}
// widget.js end

output(config);
// index.js end
```
