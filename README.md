# jasmine-coffeescript-issue
Coffeescript error messages display line number in javascript file instead of coffeescript file

Issue report here:

* https://github.com/Sanjo/meteor-jasmine/issues/168

Currently in the failing state. Just run meteor to see the error message. To get it to pass:

* meteor remove sanjo:jasmine

To get it to fail again:

* meteor add sanjo:jasmine

The following do not fail:

* meteor add mike:mocha
* meteor add sanjo:karma
