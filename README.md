LazyLoader
==========

Allows your application to load in external classes and lets you control when you want to instantiate the loaded class.

This is useful if you are building a large website and are packaging all your classes into one JavaScript file.  Sometimes you want some scripts to be deferred and requested only when it is needed.  This is when LazyLoader will be useful to you.

![Screenshot](http://www.staticdynamic.ca/reol/LazyLoader/icon.png)

How to use
----------

To load the external class and instantiate it (default behavior):

	new LazyLoader('MooClassName', [param_1, param_2, ...]);


To load the external class and instantiate it later:

	new LazyLoader('MooClassName', [param_1, param_2, ...],
	{
		autoStart: false,
		load: function()
		{
			// Do what you have to do
			// ...
			this.process(myLoader);
		}
	});


An example that uses some options:

	new LazyLoader('MooClassName', [param_1, param_2, ...],
	{
		path: '/javascript/{Klass}.js'
	});
  
Syntax
------

  new LazyLoader(mooClassName, arguments, [options])
  
Arguments
---------

  1. mooClassName - (string) Your class name and also the filename.  Please see options as to how you can change the structure of the file path.
  2. arguments - (array) Your arguments that will be passed to the constructor.
  
Options
-------

* autoStart      : (boolean) Selector to pass to element.getChildren to determine scrolling elements. Defaults to '*'.
* path           : (string) The path to your class, use {Klass} in your string to substitute it to the mooClassName.

Events
------

* onLoad : External script has been loaded.
* onProcessStart: Before processing of the loaded external script.
* onProcessEnd: After processing of the loaded external script.

Coming Soon
-----------
Please contact me if you have any suggestions or comments.

1. Additional syntax to load class dependencies, currently, you must use the load event.