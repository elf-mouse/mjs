Advanced Patterns
=================

Augmentation
------------

    var MODULE = (function (my) {
      my.anotherMethod = function () {
        // added method...
      };

      return my;
    }(MODULE));

Loose Augmentation
------------------

    var MODULE = (function (my) {
      // add capabilities...

      return my;
    }(MODULE || {}));

Tight Augmentation
------------------

    var MODULE = (function (my) {
      var old_moduleMethod = my.moduleMethod;

      my.moduleMethod = function () {
        // method override, has access to old through old_moduleMethod...
      };

      return my;
    }(MODULE));

Cloning and Inheritance
-----------------------

    var MODULE_TWO = (function (old) {
      var my = {},
          key;

      for (key in old) {
        if (old.hasOwnProperty(key)) {
          my[key] = old[key];
        }
      }

      var super_moduleMethod = old.moduleMethod;
      my.moduleMethod = function () {
        // override method on the clone, access to super through super_moduleMethod
      };

      return my;
    }(MODULE));

Cross-File Private State
------------------------

    var MODULE = (function (my) {
      var _private = my._private = my._private || {},
          _seal = my._seal = my._seal || function () {
            delete my._private;
            delete my._seal;
            delete my._unseal;
          }, // 模块加载后，调用以移除对_private的访问权限
          _unseal = my._unseal = my._unseal || function () {
            my._private = _private;
            my._seal = _seal;
            my._unseal = _unseal;
          }; // 模块加载前，开启对_private的访问，以实现扩充部分对私有内容的操作

      // permanent access to _private, _seal, and _unseal

      return my;
    }(MODULE || {}));

Sub-modules
-----------

    MODULE.sub = (function () {
      var my = {};
      // ...

      return my;
    }());
