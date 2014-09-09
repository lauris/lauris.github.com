---
layout: post
title: "Sensei Grid Testing"
category: development
---

This is daily progress update for [Sensei Grid](https://github.com/datazenit/sensei-grid). Today I spent some time to write test specifications for public data access API methods. New DOM tests were also added and test specs were dived in two files: ``apiSpec.js`` and ``domSpec.js``. Jasmine is used a testing framework and tests are run together with JSHint to ensure code quality. Tests and JSHint are also run on Travis CI server. 

Another addition was value parsers that convert string values from table cells to corresponding data type when you access cells via data API, e.g. ``getCellData``.

Development overview:

* Add value parsers to dist assets.
* Add slack notifications.
* Add tests for remaining public data api methods in apiSpec.
* Add more cell and row related tests to apiSpec.
* Add getGridData test to apiSpec.
* Fix jasmine styles config param.
* Add getCellDataByKey tests to apiSpec.
* Add getCellDataByIndex tests to apiSpec.
* Add apiSpec test suite and basic API method tests.
* Add cell value parsers and implement value parsing in getCellData API method
* Add correct column types to test data generator.
* Change domSpec title.
* Rename basicSpec to domSpec and add more dom tests.
* Build dist files from latest src changes.
* Add unicode to test data generator.
* Adjust project roadmap.
* Move Editor base class to sensei-editors.js file.
* Enable jshint on source files.
* Add build status to README.
* Add node version to travis configuration.

These changes are now published as part of a new pre-release – [v0.1.1](https://github.com/datazenit/sensei-grid/releases/tag/v0.1.1). Stay tuned, more changes coming tomorrow.