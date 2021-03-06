generator-install
===============

A generator to install remote generator

![snapshot.png](snapshot.png)

### Usage

```
  npm install -g generator-install
  
  yo install 
  yo install [pkg]
  yo install --keyword=angular
  yo install --tmpDir=./ --cfg=path/to/file
```

### Programmatic usage

```
  var generator = require('generator-install');
  generator.run(options);
```

### Args

support first argument to be `pkg`, skip prompting

`yo install generator-ngfis` is alias as `yo install --pkg=generator-ngfis`

### Options

- cfg : config file, support:
  - {Object} the config object
  - {String} JSON string of config object, given by cli args
  - {String} remote url of config file, such as a github raw url
  - {String} local path of config file
  
- keyword : filter generator

- pkg : install target
  - will use as `npm install pkg`
  - support `npm register name` / `folder path` / `git url` / `github short name`, see also `npm install` docs.
  - provide this will skip ask user to choose from config

- clean : Where to clean generator cache, default to false

- tmpDir : Where to npm install generator, default to `os.tmpDir()`

- buildin : true to use config.json of this repository , default (false) to query npm using keyword 'yeoman-generator'

### Config.json

{Array}

- name : displayName or npm register name
- pkg : optional, if provide will use as `npm install pkg`
- description / author / website : just use to display to user
  
```
[
  {
    "name": "generator-ngfis",
    "description": "ngfis generator",
    "author": "TZ <atian25@qq.com>",
    "repository": "https://github.com/ng-workflow/generator-ngfis"
  },
  {
    "name": "what ever name, pkg is github short name",
    "pkg": "ng-workflow/generator-ngfis",
    "description": "ngfis generator",
    "author": "TZ <atian25@qq.com>",
    "repository": "https://github.com/ng-workflow/generator-ngfis"
  },
  {
    "name": "what ever name, pkg is github url",
    "pkg": "https://github.com/ng-workflow/generator-ngfis",
    "description": "ngfis generator",
    "author": "TZ <atian25@qq.com>",
    "repository": "https://github.com/ng-workflow/generator-ngfis"
  },
  {
    "name": "what ever name, pkg is local url",
    "pkg": "/Usr/TZ/path/to/module",
    "description": "ngfis generator",
    "author": "TZ <atian25@qq.com>",
    "repository": "https://github.com/ng-workflow/generator-ngfis"
  }
]
```