# AngularDocuments

Purpose of maintaing this repo is to help learn the angular.
Each markdown file is the compiled version of kudvenkat's angular tutorial series. (Kudvenkat's youtube channel: https://www.youtube.com/user/kudvenka, Blog: http://csharp-video-tutorials.blogspot.com/)

Each markdown file (E.g., Angular2.md, will also include a link to original blog, from where this has been compiled)


Angular 2
======================
http://www.pragimtech.com/kudvenkat_angular2_tutorial_videos_download.aspx

## Part 1, 2, and 3 - Introduction, Setting up in Visual Studio, and Run angular app using F5 from visual studio
    
    - This 3 parts have not been compiled as the purpose of this document is to serve as a quick reference book, and the first 3 parts don't seem relevant to this context. However, at the end of the compilation of this series, I will review the document and add one or more parts if their addition would make this document easier to follow.
    
## Part 4 - Componenets
    
    i. Everything in Angular is component
        - Component is a class with a template and a decorator.
        - Component is composed of: Template (HTML / UI), Class (logic), and Decorator (to add metada to class)
        
## Part 5 - template vs templateUrl

    - Within an Angular component, HTML can be defined using either template or the templateUrl property of the component.
    
    i. template
        - When using template property, HTML can be specified within TypeScript (.ts) file enclosed in single or double quotes for one-line HTML, and within back-tick characters for multiline HTML.
        - angular recommends to use template when the HTML is 3 lines or less.
        
    ii. templateUrl
        - When HTML is more than 3 lines, templateUrl should be used.
        - With templateUrl, you can specify the path where your HTML content is available.
        
## Part 6 - Nested components

    - Angular allows for components to be nested.
    
## Part 7 - Styling Angular components

    - There are several ways to apply styling the angular component (external stylesheet, inline-styling of elements, internal styling, and using component's styles or styleUrls properties)
    - In most cases, using styleUrls would be ideal.
    - Global stylesheet files should be used only for Application / root level styling.

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

## Part 12 - Class binding in Angular

    i. Normal class usage
        - <button class='colorClass'>My Button</button>
        - colorClass has to be configure in sytlesheet file
        
    ii. Angular class binding ([class]='classesToApply')
        - <button class='colorClass' [class]='classesToApply'>My Button</button>
        - colorClass in css file, and classesToApply will be configured in .ts file (E.g., classesToApply: string = 'italicsClass boldClass';)
        - but when this component is loaded, the colorClass gets overridden by the classes specified in classesToApply
        
    iii. Add or remove single class ([class.boldClass]='applyBoldClassBoolVariable')
        - <button class='colorClass' [class.boldClass]='applyBoldClass'>My Button</button>
        - With this method, standard class (colorClass in this example) will not be affected, and boldClass will get applied conditionally based on applyBoldClass bool value in component
        - standard class can also be removed with the same method
        - <button class='colorClass boldClass italicsClass' [class.boldClass]='applyBoldClass'>My Button</button>
        
    iv. Add or remove multiple classes ([ngClass]="{'style1': true, 'style2': true}")
        -  <button class='colorClass' [ngClass]='addClasses()'>My Button</button>
        -  <button class='colorClass' [ngClass]="{'nameOfTheClassOne': boolVar, 'secondClass': someBoolCondition}">My Button</button>
        
## Part 13 - Style binding in Angular

    - This is very similar to class binding (Part 12 above). Hence, I will leave examples here, which should be self-explanatory provided you understood the class binding.
    - Standard inlie styling: <button style="color:red">My Button</button>
    - <button style='color:red' [style.font-weight]="isBold ? 'bold' : 'normal'"> My Button </button>
    - <button style='color:red' [style.font-size.px]="fontSize"> My Button </button> (fontSize in .ts - I.e., fontSize: number = 30;)
    - <button style='color:red' [ngStyle]="addStyles()"> My Button </button>
    
## Part 14 - Event binding in Angular

    - One-way data binding that we looked at so far (Interpolation, property binding, attribute binding, class binding, style binding) flows data from Component to View.
    - Event binding is a type of data binding that flows data (mainly events) from View to Component (E.g., onClick etc.)
    - <button (click)="onClick()"> Click me </button>
    
## Part 15 - Two-way data binding in Angular

    - Name : <input [(ngModel)]='name'> 
    - Note: ngModel requires FormsModule to be imported in AppModule
