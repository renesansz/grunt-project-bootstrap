Grunt Project Bootstrap
----------------------------
This is a simple project bootstrap for web projects that will be using [Grunt JS](gruntjs.com/getting-started). This is folder a structure for organizing your Grunt task(s) and config(s).

## Project Structure
* grunt/
    - configs/ - **This is where you put the grunt task config(s)**
    - commands/ - **This is where you declare your grunt commands**

## How do you add in Grunt task configs?
It's simple! you'll just create a JavaScript file for the grunt task that you want to configure.

eg: [Grunt Contrib Watch](https://www.npmjs.com/package/grunt-contrib-watch)
```
'use strict';

module.exports = {

    // Watch over CSS files
    css: {
        files: ['css/*.css'],
        tasks: ['minify']
    },

    // Watch over JS files
    js: {
        files: ['js/*.js'],
        tasks: ['jshint']
    }

};
```
Very easy right? So if you want to create another config file for a certain task (eg: [Grunt Contrib Connect](https://www.npmjs.com/package/grunt-contrib-connect)), you simply create **connect.js** file and inside is the configuration. make sure to do still `module.exports = {};`
**REMEMBER: always name the files after their corresponding grunt tasks  verbatim**, so a config file for *ngAnnotate* task should be named *ngAnnotate.js*

## How do you add Grunt commands?
Still, it's very simple! You'll just have to create a JavaScript file for a corresponding **Grunt command**.
For the example, we'll create for the default command.
```
'use strict';

module.exports = function (grunt) {

    grunt.registerTask('default', ['jshint', 'minify']);

};
```
VERY EASY still right? So now we can do `grunt` in our command line and it will execute the `jshint` and `minify` tasks.
**REMEMBER: if you want to create another command, just simply name it after the command that you are creating** (eg: `grunt build` = *build.js*)

## What is Gruntfile.js now?
Let's say you want to create constant variable(s) (eg: ports, folder paths, etc.). Then you can modify your *Gruntfile.js* to add constant variable(s)

```
    var gruntConf = {
        // Constant Variables
        // ------------------
        // 
        // This will allow us to access them through <%= variable_name %>
        // eg: <%= foo %>
        data: {

            // Grunt Directories
            grunt_configc_dir: 'grunt/configs',
            grunt_tasks_dir: 'grunt/commands',

        }
    };
```
By looking in the **gruntConf data property** you can add constant variable(s) that you like and still you can access them in to your task configs by using the `<%= variable_name_here %>` annotation, **make sure you separate them with commas (,)**

------------------------------------------------------------------------------------
**License: MIT**
**Feel free to clone and make it as your bootstrap for your projects**