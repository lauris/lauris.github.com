---
layout: post
title: "Sensei Grid Daily Progress"
category: development
image: /images/blog/sensei-grid-screenshot.png
---

Today was a big day for [Sensei Grid](https://github.com/datazenit/sensei-grid), an open source data grid in JavaScript/HTML I am currently working on. The project reached 2nd place in GitHub's [Trending repository list](https://github.com/trending) (1st between JavaScript repositories). GitHub sends out daily emails about new Trending repos and that resulted in even more traffic and followers to Sensei Grid. I was happy to see project's community growing steadily.

<!-- more -->

[![Sensei Grid screenshot](https://camo.githubusercontent.com/0cbeccc04788461c17455e1a75d7ca4254580817/687474703a2f2f6c61757269732e6769746875622e696f2f696d616765732f626c6f672f73656e7365692d677269642d73637265656e73686f742e706e67)](https://github.com/datazenit/sensei-grid)

I continued my work on the project and made it available as [a Bower package](http://bower.io/search/?q=sensei-grid). You can now install Sensei Grid with just one simple command ``bower install sensei-grid``. I also cleaned up the repository, added some basic tests and testing infrastructure. I got confused between countless options for JS project testing, but finally decided to use good old Jasmine with PhantomJS and Grunt. Tests can be easily executed by just running ``grunt test``.  

Sensei Grid is now hooked with Travis CI platform and build status is always visible in the README.md file. Check out [Sensei Grid at Travis CI](https://travis-ci.org/datazenit/sensei-grid). Currently Travis is configured to just run tests, but I will add code hinting and other goodies soon.

Daily development overview:

* Add build status to README.
* Add node version to travis configuration.
* Add grunt installation to travis before_install directive.
* Add basic test specs and helpers.
* Add jasmine deps to package.json.
* Add jasmine test runner to gruntfile.
* Add .grunt to gitignore.
* Add white background to custom editor's select element.
* Add initial Gruntfile.
* Add compiled dist assets.
* Fix references to new dist files.
* Add global exports to core js files.
* Add cell padding.
* Add package.json deps.
* Add CustomEditor to example file.
* Move assets to src folder.
* Add .travis.yml file for CI.
* Add package.json file for npm.
* Add proper version to bower.json.
* Add main files to bower.json.
* Fix name of package.
* Add default table styling to the main css to avoid twitter bootstrap dependecy.
* Remove bootstrap from bower's deps.
* Add sub-directories to bower's ignored paths.
* Add bower components and bower.json.
* Cleanup main CSS file.
* Fix production clause.