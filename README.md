# JavaScript Module Pattern

	var UTIL = (function (parent, $) {
	  var my = parent.ajax = parent.ajax || {};
	
	  my.get = function (url, params, callback) {
	    // ok, so I'm cheating a bit :)
	    return $.getJSON(url, params, callback);
	  };
	
	  // etc...
	
	  return parent;
	}(UTIL || {}, jQuery));
