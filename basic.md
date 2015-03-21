The Basics
==========

Anonymous Closures
------------------

    (function () {
      // ... all vars and functions are in this scope only
      // still maintains access to all globals
    }());

Global Import
-------------

    (function ($, YAHOO) {
      // now have access to globals jQuery (as $) and YAHOO in this code
    }(jQuery, YAHOO));

Module Export
-------------

    var MODULE = (function () {
      var my = {},
          privateVariable = 1;

      function privateMethod() {
        // ...
      }

      my.moduleProperty = 1;
      my.moduleMethod = function () {
        // ...
      };

      return my;
    }());
