# jquery.hook

> Provides the ability to hook into any `jQuery.fn[ method ]` with `onbeforeMETHOD`, `onMETHOD`, and `onafterMETHOD`s. 


Pass in a string or array of method names you want to hook into with `onbefore`, `on`, or `onafter` events. Example: 

	jQuery.hook('show');
	jQuery(selector).bind('onbeforeshow', function (e) { alert(e.type); });
	jQuery(selector).show() -> alerts 'onbeforeshow'


	jQuery.hook('show hide');
	jQuery(selector)
		.bind('onbeforeshow', function (e) { alert(e.type);})
		.bind('onshow', function (e) { alert(e.type);})
		.bind('onaftershow', function (e) { alert(e.type);})
		.bind('onafterhide', function (e) { alert("The element is now hidden.");});
		
	jQuery(selector).show();
		-> alerts 'onbeforeshow' then alerts 'onshow', then alerts 'onaftershow'
		
	jQuery(selector).hide();
		-> after the element is hidden alerts 'The element is now hidden.'

You can also unhook what you've hooked into by calling `jQuery.unhook()` passing in your string or array of method names to unhook.

	jQuery.unhook('show hide');