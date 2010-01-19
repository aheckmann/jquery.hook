# jquery.hook

> jQuery.hook provides the simple ability to hook into/around any `jQuery.fn[ method ]` with custom events. These events can be listened to just like any other jQuery events: 

	jQuery.hook('show');
	jQuery(selector).bind('onbeforeshow', function () {
		// this is fired before show() is fired
	});

Just pass in a string or array of method names you want to hook and when you call the method, three additional events are fired. Here is the new execution flow:

1. onbeforeMETHOD event fires
2. onMETHOD event fires
3. original METHOD fires
4. onafterMETHOD event fires
 
Example: 

	jQuery.hook('show hide');
	jQuery(selector)
		.bind('onbeforeshow', function (e) { alert(e.type);})
		.bind('onshow', function (e) { alert(e.type);})
		.bind('onaftershow', function (e) { alert(e.type);})
		.bind('onafterhide', function (e) { 
			alert("The element is hidden");
		})
	;

	jQuery(selector).show().hide();
		-> alerts 'onbeforeshow', 
			then alerts 'onshow', 
			then alerts 'onaftershow', 
			and after hide fires alerts 'The element is hidden'


You can also unhook what you've hooked into by calling `jQuery.unhook()` passing in your string or array of method names to unhook.

Example:

	jQuery.unhook('show hide');

