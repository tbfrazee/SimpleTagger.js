#SimpleTagger.js
A lightweight Javascript function that turns any input or textarea field into an autocomplete or multiselect tagger. The user gets an easy-to-use interface with autocomplete dropdown, tag selection, and tag removal. The developer just provides the selectable values.

SimpleTagger can take an array or JS object of values, or a url to a server route that will return JSON of values, either as an array or object.

When used as a tagger, SimpleTagger can provide an array of selected values as a Javascript method (see below), or it can automatically put all values into a (typically hidden) input field as comma-delimited values for easy form submission.

##Installation
Simply copy SimpleTagger.js and SimpleTagger.css to your server, and import both to your page.
For SASS users, you can use SimpleTagger.scss instead of SimpleTagger.css to integrate as a SASS import.

##Usage
Example Usage: let tagger = new SimpleTagger('inputElement', 'hiddenElement', {values: ['autocomplete', 'values', 'go', 'here']);

**inputEl**     A DOM reference to an input or textarea element to which the tagger should be attached
**hiddenEl**    A DOM reference to an input or textarea (typically hidden) that will store the comma-delimited results for submission
**settings**    An object of settings, see below. At very least, either 'url' or 'values' is required.

###Settings:
     **url:**                A URL target to make AJAX requests to get autocomplete values. If this value is defined, a request will be sent to retrieve values.
                         The URL includes a query key 'inputVal' that contains the text entered so far. The server should respond with JSON including a value called "values"
                         that contains an array or object of key-value pairs that represents the possible autocomplete values.
     **ajaxMethod:**         HTTP method to get autocomplete values. Only used if url is defined. Default: "GET".
     **values:**             An array or object of key-value pairs that represents the possible autocomplete values. Only used if settings.url is not defined.
     **allowDuplicates:**    True to allow the same tag to be selected multiple times. False to remove an option once it's selected. Noop if settings.autocompleteOnly is true.
     **autocompleteOnly:**   True to remove tagging functionality. Autocomplete selections will simply be applied as the value of inputEl.
     **autocompleteAppend:** True to append multiple autocomplete values together as the value of inputEl, delimited by a comma and space. Only applies if settings.autocompleteOnly is true.

###Methods:
	**SimpleTagger.on(eventName, function):**
		Specifies a handler function for a named event. Use to add custom behaviors.
		Events (arguments):
			onACUpdate (current input value)
			autoCompleteClick (clicked value)
			onTag (clicked value)
			
	**SimpleTagger.destroy():**
		Removes the SimpleTagger from the DOM and removes event handlers from the input element.