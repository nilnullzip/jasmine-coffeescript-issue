# jasmine-coffeescript-issue
Coffeescript server error messages display line number in javascript file instead of coffeescript file

Issue report here:

* https://github.com/meteor-velocity/meteor-internals/issues/2

Currently in the failing state. Just run meteor to see a server stack trace with incorrect line number display. Also run meteor debug and see that the coffeescript file is available to the node debugger.

To get it to work:

* meteor remove velocity:meteor-internals

To get it to fail again:

* meteor add velocity:meteor-internals

The line numbers in the stack trace can be made to work by commenting out the following lines in packages/meteor-internals/tools/files.js starting at line 33:

<pre>
sourcemap_support.install({
  // Use the source maps specified to runJavaScript instead of parsing source
  // code for them.
  retrieveSourceMap: retrieveSourceMap,
  // For now, don't fix the source line in uncaught exceptions, because we
  // haven't fixed handleUncaughtExceptions in source-map-support to properly
  // locate the source files.
  handleUncaughtExceptions: false
});
</pre>

However in that case the coffeescript file is not available to the node debugger.
