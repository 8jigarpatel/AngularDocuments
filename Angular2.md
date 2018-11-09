Angular 2
======================
http://www.pragimtech.com/kudvenkat_angular2_tutorial_videos_download.aspx

## Part 8 & 9 - Data-Binding: One-way (from Component to View, from View to Component), Two-way

	i. Interpolation [from Component to View]
		- {{ varName }}
		- <img src='{{imagePath}}'/> 
		- concatenation is possible; {{ "Var is: " + varName }}
		- expressions can be specified; {{ 10 + 20 + 20 }} will render 50
		- Template expressions; {{ boolCondition ? "condition satisfies" : "condition does not satisfy" }}
		- methods can be called; {{ getUserName() }}
		- cannot be used when binding non-string value to HTML element's attribute

	ii. Property Binding [from Component to View]
		- <img [src]='imagePath'/>
		- concatenation cannot be done
		- can be used for non-string value binding- <button [disabled]='isBtnDisabled'> Click me </button>
		
	Note: Interpolation gets converted into property binding by Angular. both the techniques protect us from malicious content and render the content harmlessly.

## Part 10 - HTML attribute vs DOM property

	i. DOM (Document Object Model)
		- when browser loads a page it creates the DOM of the page
		- DOM could be thought of as an API for HTML
		- Angular, JS etc can be used to access and manipulate the HTML using their corresponding DOM
		- DOM contains HTML elements as objects, their properties, methods, and events and it is a standard for accessing, modifying, adding or deleting HTML elements
		
		<button [disabled]='isDisabled'>Click Me</button>
		- Here, it looks like we are binding to button's disabled 'attribute of button element' (in HTML). This is not true. We are actually binding to the disabled 'property of the button object' (in DOM).
		
		Note: Angular data binding is all about binding to DOM OBJECT PROPERTIES and NOT HTML ELEMENT ATTRIBUTES.
		
	ii. HTML Attribute vs DOM Property
		- Attributes are defined by HTML, where as properties are defined by DOM
		- Attributes initialize DOM properties. Once the initialization is done, the attributes' job is done.
		- Property values can change, attribute values cannot.
		
		Note: Most element attributes have corresponding dom properties, but some don't. E.g., colspan & rowspan.
		
## Part 11 - Angular attribute binding
	
  i. This can be used where property binding / interpolation cannot help (E.g., rowspan / colspan). But Angular team recommends to use property binding when possible, and use attribute binding when there is no corresponding element property to bind.
	
	ii. Using interpolation (<th colspan="{{columnSpan}}">) or property binding (<th [colspan]="columnSpan">) will result in an error: "Can't bind to 'colspan' since it isn't a known property of 'th'"
	
	iii. Angular attribute binding: <th [attr.colspan]="columnSpan"> or <th attr.colspan="{{columnSpan}}">
