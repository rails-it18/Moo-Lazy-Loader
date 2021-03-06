ScriptLoader
============

Allows your application to selectively load classes and lets you control when you want to instantiate the loaded class.

This is useful if you are building a large website and are packaging all your classes into one JavaScript file.  Sometimes you want some scripts to be deferred and requested only when they are needed.  This is when ScriptLoader will be useful to you.

NEW (2015/SEP/22) - 1.4 Mootools 1.5.2 Support.

How to use
----------

To load the external class and instantiate it (default behavior):

	new ScriptLoader('MooClassName', [arg_0, arg_1, ...]);


To load the external class and instantiate it later:

	var loader = new ScriptLoader('MooClassName', [arg_0, arg_1, ...],
	{
		autoStart: false
	});
	loader.addEvent('load', function()
	{
		// Code
		// ...
		this.process(myLoader);
	}.bind(loader));

To get the reference of an instance:

	var loader = new ScriptLoader('MooClassName', [arg_0, arg_1, ...]);
	loader.addEvent('processEnd', function()
	{
		this.getInstance().doSomething(); // doSomething is an instance method.
	}.bind(loader));

An example that uses some options:

	new ScriptLoader('MooClassName', [arg_0, arg_1, ...],
	{
		path: '/javascript/{Klass}.js'
	});
	
NEW - To load multiple classes at once

	var loader = new ScriptLoader.Multiple(
	[
		'GoogleMaps.Control',
		'GoogleMaps.Control.Type',
		'GoogleMaps.Control.Zoom',
		'GoogleMaps.Marker'
	],
	{
		path: '/javascript/{Klass}.js'
	}); 
	loader.addEvent('load', this.process_after_loading.bind(this));
  
Syntax
------

  new ScriptLoader(mooClassName, arguments, [options])
  
Arguments
---------

  1. mooClassName - (string) Your class name and also the filename.  Please see options as to how you can change the structure of the file path.
  2. arguments - (array) Your arguments that will be passed to the constructor.
  
Options
-------

* autoStart      : (boolean) Whether or not your class will be instantiated once it's loaded.  Defaults to true
* path           : (string) The path to your class, use {Klass} in your string to substitute it to the mooClassName.  Defaults to same path.

Events
------

* onLoad : External script has been loaded.
* onProcessStart: Before processing of the loaded external script.
* onProcessEnd: After processing of the loaded external script.

Release Notes
-------------

* 1.4    : MooTools 1.5.2 support. Renamed from LazyLoader to ScriptLoader
* 1.3    : Now allows any numbers of arguments. Improved support for MooTools 1.2 and 1.3.
* 1.2    : Allows loading of multiple classes.
* 1.1.1  : MSIE7 fix.
* 1.1    : Allows multiple instances.

