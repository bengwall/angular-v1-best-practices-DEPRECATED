###Angular Guide and Best Practices


#About this Guide

AngularJS provides a broad set of capabilities which can dramatically accelerate the development of Single Page Web Applications ("SPAs").  Both a pro and a con is the flexibility of using AngularJS as how you need it.  AngularJS does not tie you down to a specific, tightly dictated code and framework structure.  As a result, we need some guidelines to which give us a starting point and context to create our applications.  The purpose of this guide is to provide these guidelines and other guidance which developers should be aware of when developing Angular applications.  

This guide is based on many resources.  Here are some of the resources which have been most helpful:

0. [Angular Style Guide by Todd Motto](https://github.com/toddmotto/angularjs-styleguide)
0. [ng-boilerplate](http://joshdmiller.github.io/ng-boilerplate/#/home)
0. [The old way, the Angular way](http://thesmithfam.org/blog/2012/12/02/angularjs-is-too-humble-to-say-youre-doing-it-wrong/)
0. [AngularJS Best Practices: I’ve Been Doing It Wrong! (Part 1 of 3)](http://www.artandlogic.com/blog/2013/05/ive-been-doing-it-wrong-part-1-of-3/)
1. [AngularJS Best Practices: I’ve Been Doing It Wrong! (Part 2 of 3)](http://www.artandlogic.com/blog/2013/05/angularjs-best-practices-ive-been-doing-it-wrong-part-2-of-3/)
2. [AngularJS Best Practices: I’ve Been Doing It Wrong! (Part 3 of 3)](http://www.artandlogic.com/blog/2013/05/angularjs-best-practices-ive-been-doing-it-wrong-part-3-of-3/)
0. [GitHub angularjs-style-guide](https://github.com/mgechev/angularjs-style-guide) 
0. http://trochette.github.io/Angular-Design-Patterns-Best-Practices
0. [Some tips from the Angular team](https://github.com/angular/angular.js/wiki/FAQ)
0. The book [Mastering Web Application Development with AngularJS](http://www.amazon.com/Mastering-Web-Application-Development-AngularJS/dp/1782161821) and its companion app [angular-app](https://github.com/angular-app/angular-app).  You can read and search the book [online](http://books.google.com/books?id=mZXjwz5X08EC&pg=PT125&lpg=PT125&dq=angularjs+spanning+module+across+many+files&source=bl&ots=T4HZQQP5RX&sig=GP1K1rK-4YXUgMSn2jWksavMCBo&hl=en&sa=X&ei=ZtX8UoeEJci6yAHTvoBA&ved=0CDwQ6AEwAg#v=onepage&q=angularjs%20spanning%20module%20across%20many%20files&f=false).
0. [Google's AngularJS Style guide](https://google-styleguide.googlecode.com/svn/trunk/angularjs-google-style.html).  (This is, however, skewed because it is written for Google's internal environment.)
0. [Best Practice Recommendations for Angular App Structure](https://docs.google.com/document/d/1XXMvReO8-Awi1EZXAXS4PzDzdNvV6pGcuaF4Q9821Es/pub).  This heavily leans on Google's JavaScript Style Guide.

### Learning Angular
This guide NOT intended to give an overview of how Angular works.  This guide assumes that the reader has familiarity with AngularJS.  There are many external resources already available which the developer can use to quickly get understand Angular.  We would recommend following these steps:

1. Watch some introductory videos:
    * John Linquists [online tutorial](http://www.youtube.com/watch?v=uFTFsKmkQnQ#t=22)
    * [Dan Wahlin at the AngularJS 2014 Conference](https://www.youtube.com/watch?v=tnXO-i7944M)
0. Read some introductory posts:
    * [3 Reasons to Choose AngularJS for Your Next Project](http://code.tutsplus.com/tutorials/3-reasons-to-choose-angularjs-for-your-next-project--net-28457)
    * [Fun with AngularJS!](http://devgirl.org/2013/03/21/fun-with-angularjs)
    * [Everything you need to understand to start with AngularJS](http://stephanebegaudeau.tumblr.com/post/48776908163/everything-you-need-to-understand-to-start-with)
    * [5 Awesome AngularJS Features](http://code.tutsplus.com/tutorials/5-awesome-angularjs-features--net-25651)
0. Go through some more in depth tutorials
	* [Course sponsored by Google](http://campus.codeschool.com/courses/shaping-up-with-angular-js/intro)
    * [Read through the AngularJS Team's tutorial](http://docs.angularjs.org/tutorial)
    * [Go though John Linquists's online videos](https://egghead.io/tags/AngularJS)
    * Ingo Rammer and Christian Weyer's ["continuously deployed ebook"](http://henriquat.re/)
    * Great blog post on Promises:  [Overview](http://liamkaufman.com/blog/2013/09/09/using-angularjs-promises/), [Chaining](http://solutionoptimist.com/2013/12/27/javascript-promise-chains-2/)
0. Read the book [Mastering Web Application Development with AngularJS](http://books.google.com/books?id=mZXjwz5X08EC&pg=PT125&lpg=PT125&dq=angularjs+spanning+module+across+many+files&source=bl&ots=T4HZQQP5RX&sig=GP1K1rK-4YXUgMSn2jWksavMCBo&hl=en&sa=X&ei=ZtX8UoeEJci6yAHTvoBA&ved=0CDwQ6AEwAg#v=onepage&q=angularjs%20spanning%20module%20across%20many%20files&f=false) online.
0. Experiment with Angular on [jsFiddle](http://jsfiddle.net/basarat/V9sYB/).
0. Go through some angular UI libraries such as [Angular Material](https://material.angularjs.org/#/) and [AngularUI](https://angular-ui.github.io/)


#Table of content

* [Introduction to AngularJS](#introduction-to-angularjs)
* [Directory Structure](#directory-structure)
* [AngularJS Components](#angular-components)
    * [Modules](#modules)
    * [Controllers](#controllers)
    * [Services](#services)
    * [Filters](#filters)
    * [Directives](#directives)
    * [Domain Models](#domain-models)
    * [Templates](#templates)
* [Naming Examples Summary](#naming-examples-summary)
* [REST Calls](#rest-calls)
* [Other AngularJS Tips](#other-angularjs-tips)
* [Other Useful Links and Blogs](#other-useful-links-and-blogs)
* [Misc JavaScript Tips](#misc-javascript-tips)
* [Development Workflow and Build Process](#development-workflow-and-build-process)


# Introduction to AngularJS

As Single Page Application (SPA) development become popular, there has become a need for MVC type frameworks on the client side.  These frameworks are needed to provide separation of concerns and other features we have become accustomed in backend frameworks.  Typical web application front-end development concentrated on DOM selection, traversal, and manipulation.  jQuery made this development easier, but the result was still tightly coupled HTML and JS which is difficult to maintain.  Many CSS classes were not used for styling, but only for DOM selection. JavaScript typically was unstructured and littered with CSS selector logic.

AngularJS gives us a MVC framework including routing, controllers, templating, data binding, façade services, and integration capabilities.  AngularJS also includes other capabilities such as animation and validation which negate the need for jQuery altogether.  The result is an application which is better structured, less costly to develop and maintain, more testable, supports modularization and reusability.

[Wikipedia has a very good explanation of AngularJS:](http://en.wikipedia.org/wiki/AngularJS)

> AngularJS is built around the belief that declarative programming should be used for building user interfaces and wiring software components.  The framework adapts and extends traditional HTML to better serve dynamic content through two-way data-binding that allows for the automatic synchronization of models and views. As a result, AngularJS deemphasizes DOM manipulation and improves testability.

> Design goals:
• Decouple DOM manipulation from application logic. This improves the testability of the code.
• Regard application testing as equal in importance to application writing. Testing difficulty is dramatically affected by the way the code is structured.
• Decouple the client side of an application from the server side. This allows development work to progress in parallel, and allows for reuse of both sides.
• Guide developers through the entire journey of building an application: from designing the UI, through writing the business logic, to testing.

> Angular follows the MVC pattern encourages loose coupling between presentation, data, and logic components. Using dependency injection, Angular brings traditional server-side services, such as view-dependent controllers, to client-side web applications. Consequently, much of the burden on the backend is reduced, leading to much lighter web applications.

# Directory structure

Angular applications are not tied to any one particular directory structure and there are many differing opinions in the development community.  The following directory structure, however, follows one of the more prevalent structures for Angular applications and SPA applications in general.  Using this structure will allow your team to utilize more advanced testing and build capabilities as our development processes for SPA applications mature.  

```

└── src/ (or WebApp for Java projects)
    ├── app/
    │   ├── <page-1>/
    │   │   ├── <page-1>.js
    │   │   ├── <page-1>.spec.js
    │   │   └── <page-1>.tpl.html
    │   ├── <page-grouping-1>/
    │   │   ├── <page-2>/
    │   │   │   ├── <page-2>.js
    │   │   │   ├── <page-2>.spec.js
    │   │   │   └── <page-2>.tpl.html
    │   │   └── <page-3>/
    │   │       ├── <page-3>.js
    │   │       ├── <page-3>.spec.js
    │   │       └── <page-3>.tpl.html
    │   ├── <page-grouping-2>/
    │   │   ├── <page-4>.js
    │   │   ├── <page-4>.spec.js
    │   │   ├── <page-4>.tpl.html
    │   │   ├── <page-5>.js
    │   │   ├── <page-5>.spec.js
    │   │   └── <page-5>.tpl.html
    │   ├── app.js
    │   └── app.spec.js
    ├── assets/
    │   ├── css/
    │   ├── fonts/
    │   └── img/
    ├── common/
    │   ├── directives/
    │   │   ├── <directive-1>/
    │   │   │   ├── <directive-1>.js
    │   │   │   ├── <directive-1>.spec.js
    │   │   │   └── <directive-1>.tpl.html
    │   │   ├── <directive-2>.js
    │   │   └── <directive-3>.js
    │   ├── filters/
    │   │   ├── <filter-1>.js
    │   │   └── <filter-2>.js
    │   ├── models/
    │   │   ├── <model-1>.js
    │   │   └── <model-2>.js
    │   ├── services/
    │   │   ├── <service-1>.js
    │   │   └── <service-2>.js
    ├── static
    │   ├── <static-page-1>.html
    │   └── <static-page-2>.html
    └── index.html
```

* Within this structure there is flexibility to arrange page directories as project teams most efficient.  Large projects will have different organizational needs then smaller projects.
* The `.spec.js` files are the unit tests. The build system will scan the directory structure and pick up all the tests automatically.
* The `.tpl.html` files are HTML templates.
* The `app` and `common` folders contain AngularJS-specific code.  `app` for the pages and `common` for directives, filters, and services.
* The `assets` and `static` folders contain AngularJS-agnostic artifacts.  `static` contains static html files.



# Angular Components

###Modules

* **DEFINITION:** Angular applications are structured in modules. Think of modules as namespaces which can wrap application code pertaining to specific functionality.  Modules can specify other modules on which they depend.  This injection capability allows for re-use and structure.
    * Modules allow you to separate your application in small, easily testable, components.
    * Modules help keep the global namespace clean. 
* **NAMING:** Modules should be named with lowerCamelCase.  As package names in Java, you can nest Modules by using namespacing like: `a.b`.
    * For Controllers use `<app-prefix>.<page-name>`.  Examples: `xx.personDetails`, `xx.about`
    * For Services use `<app-prefix>.<service-name>Service`.  Examples: `xx.personService`, `xx.addressService`
    * For Filters use `<app-prefix>.<filter-name>Filter`.  Example: `xx.centsFilter`
    * For Directives use `<app-prefix>.<directive-name>`.  Examples: `xx.alert`
    * For Models use `<app-prefix>.<model-name>`.  Examples: `xx.person`, `xx.address`
* **GUIDELINES:** 
    * As a general practice, define one Module per JavaScript file.  When you have one Module spread among multiple files you need to be concerned about the load order of those files.


###Controllers

* **DEFINITION:** As in a typical MVC framework, the Controller links the view to the model.  Their main function is to expose the Model data and handler functions to the View.  Usually these handlers are triggered by user interactions such as clicking on a button. A handler will normally call through to an appropriate Model function to run the actual business logic based on the events from the View.
* **NAMING:** Controllers should be named with upperCamelCase.  Name the Controller based on its function (for example shopping cart, person details) and append `Controller` to the end. The controllers are named UpperCamelCase (`ShoppingCartCtrl`, `PersonDetailsCtrl`, etc.).
* **GUIDELINES:**
    * Make the controllers as lean as possible.
        * Move business logic into facade services.
        * Abstract commonly used functions into services or model functions.
        * When you need to format data encapsulate the formatting logic into [Filters](#filters).
        * Do not manipulate DOM in your controllers, use [Directives](#directives).
    * Controllers can be reused between several similar pages.
    * Use the [Controller as](http://www.thinkster.io/pick/GmI3KetKo6/angularjs-experimental-controller-as-syntax) syntax and as the first line of your controller add the line `var model = this`.  This will place the controller object into the Scope which you can use as your View Model.  As a general rule of thumb, you should avoid direct bindings to the Scope's properties, but instead bind to an object bound the Scope.  Per Google, this also reduces the risk around prototypal inheritance masking primitives.  Here is an excellent [video](https://egghead.io/lessons/angularjs-experimental-controller-as-syntax) which explains this concept.

* **EXAMPLE:**  
Pathname: `/app/persons/person-details.js`
```JavaScript
"use strict";
angular.module( 'xx.personDetails', [
    'xx.service.personService'
])

.config(['$stateProvider', 
	function config( $stateProvider ) {
		$stateProvider.state( 'personDetails', {
			url: '/personDetails',
			views: {
				"main": {
					controller:  'PersonDetailsCtrl as model',
					templateUrl: 'app/personDetails/person-details.tpl.html'
				}
			}
		});
	}
])

.controller( 'PersonDetailCtrl', ['$location',
	function PersonDetailCtrl( $location ) {
		var model = this;
		...
	}
]);
```



###Services

* **DEFINITION:** In an Angular application, the Business Service Layer and Integration Layer are comprised of AngularJS Services.  Services are singletons which can used in Controllers, Filters, Directives, Resources and other Services.
* **NAMING:** Services should be named with upperCamelCase.  *See the example below.*
* **GUIDELINES:** 
    * Encapsulate business logic and integration logic in Services, not in Controllers
* **EXAMPLE:**
Pathname: `/common/services/xx-person-service.js`
```JavaScript
"use strict";
angular.module( 'xx.service.personService', [
    'restangular'
])

.factory('PersonService', ['Restangular',
	function(Restangular) {
		
		var PersonService = {
			retrieveCities : function(zipCode) {
		        return Restangular.one('locations/cities',zipCode).get();
			}
			retrieveAddressMatches : function(address, addressType) {
			    var url = Restangular.all('locations/addresses');
				var request = {};
				request.Address = address;
				request.addressType = addressType;
				return url.post(request);
			}
		}
		
		return PersonService;
	}
])
```

###Filters

* **DEFINITION:** Filters format the value of an expression for display to the user. Use filters when the data format that is being stored is different than the format you want displayed.  Filters can be used in Templates, Controllers or Services.  Angular has many built in filters, and you can easily create your own filters.
* **NAMING:** Filters should be named with lowerCamelCase
    * Use the custom prefix `xx` to prevent name collisions with third-party libraries.
* **GUIDELINES:** 
    * Make your filters as light as possible. They are called often during the `$digest` loop so creating a slow filter will slow down your app.
* **EXAMPLE:**
Pathname: `/common/filters/xx-filters.js`
```JavaScript
"use strict";
angular.module("xx.filters", [])

.filter('CentsFilter', function() {
	// return only the cents from the dollar amount
	return function(amt) {
		var padLeft = function(number, length) {
			var s = '' + number;
			while (s.length < length) s = '0' + s;
			return s;
		}
		
		var cents = Math.round(amt*100)%100;
		return padLeft(cents, 2);
	};
})
```
```
{{10.91 | xx-cents-filter:'city'}} cents       <!-- Returns '.91 cents' -->
```
* Note that, in this example, the module name is not 'xx.centsFilter'.  In this case, we will include all custom filters in this module, so we have named it generically.


###Directives

* **DEFINITION:** At a high level, directives custom DOM elements or attributes that attach a specified behavior to that DOM element or even transform the DOM element and its children.  Angular comes with a set of these directives built-in. Custom directives can be created for Angular to use. When Angular bootstraps your application, the HTML compiler traverses the DOM matching directives against the DOM elements.   
> Directives can be complex to create because the developer needs to understand how Angular handles binding under the covers.  Directives will have a simplier design in Angular 2.0.
> 
Directives are the key to the power of Angular.  The name **AngularJS** originated from the angle brackets used in the DOM for these directives.  Angular is defined as being *declarative* because it marks up the DOM, whereas JQuery's method of manipulation is *imperative* because the functionality is expressed purely in code.

* **NAMING**: Directives SHOULD be named in lowerCamelCase
    * Use the custom prefix `xx` to prevent name collisions with third-party libraries.
* **GUIDELINES:** 
    * DOM manipulations SHOULD be done only through directives.
    * Create an isolated scope when you develop reusable components.
    * Use directives as attributes or elements instead of comments or classes, this will make your code more readable.
    * Do not forget to use `$sce` when you should deal with untrusted content.
* **EXAMPLE:**
Pathname: `/common/directives/xx-alert.js`
```JavaScript
"use strict";
angular.module('xx.alert', [])

.controller('AlertCtrl', function ($scope, $attrs) {
	$scope.closeable = 'close' in $attrs;
})

.directive('xxAlert', function () {
 	return {
		restrict:'EA',
		controller:'AlertCtrl',
		template:
			"<div class='alert' ng-class='\"alert-\" + (type || \"warning\")'>\n" +
			"	<button ng-show='closeable' type='button' class='close' ng-click='close()'>&times;</button>\n" +
			"	<div ng-transclude></div>\n" +
			"</div>\n",
		transclude:true,
		replace:true,
		scope: {
			type: '@',
			close: '&'
		}
	};
});
```


###Domain Models
* **DEFINITION:** Angular does not require the use of models, nor does it dictate how build your models.  Models are completely optional in Angular, but I would highly recommend you use them for the following reasons:
	* Domain models will help you organize your app because they model the real world.  Models go beyond POJO's in that they not only allow you to store data in an object, but methods also.  A Person model, for instance, will not only store data about the person, but also will know how to persist, load and rate itself.  Most of my business layer disappeared because most of the methods became methods in the models. 
	* JavaScript will quickly become more object orientated.  OO features are being added with EM6.  
* **NAMING:** Filenames SHOULD be the model name.  For example,  `person.js, address.js`.
* **GUIDELINES:** 
    * There are many ways to create models in JavaScript.  I have iterated over several methods while striving to achieve a simple and maintainable design.  The example below is what I came up with.
* **EXAMPLE:**
```JavaScript
"use strict";
// Based on:
//  https://medium.com/opinionated-angularjs/angular-model-objects-with-javascript-classes-2e6a067c73bc
//  http://javascriptweblog.wordpress.com/2010/06/07/understanding-javascript-prototypes/
//  http://www.webdeveasy.com/angularjs-data-model/
//  http://www.htmlgoodies.com/beyond/javascript/some-javascript-object-prototyping-patterns.html
//  http://www.htmlgoodies.com/beyond/javascript/object.create-the-new-way-to-create-objects-in-javascript.html

angular.module("xx.model.person", [
	'xx.service.person',
	'xx.model.activity'
])

.factory('Person', 
	function($rootScope, PersonService, Activity) {

		// Private functions
		// var _privateFnc = function(){};

		// Constructor, with class name
		function Person(startObj) {
			var self = this;
			if (startObj) angular.extend(self, startObj);
		};

		// Public methods, assigned to prototype
		Person.prototype = {
		   	loadById: function(personId) {
		   		var self = this;
				return PersonService.loadById(personId).then(Person.apiResponseTransformer).then(function(person){
					return angular.extend(self, person);
				});
			},
			save: function() {
				return PersonService.save(this);
			},
			toggleFavorite: function(){
				this.favorite = !this.favorite;
				return this.save();
			},
			addOrUpdateActivity:  function(activity){
				return PersonService.addOrUpdateActivity(this, activity)
			}
		};
		
		// Static methods, assigned to class (Instance ('this') is not available in static context)
		Person.build = function(data){
			var person = Person(data);
			person.activities = Activity.apiResponseTransformer(person.activities);
			return new person;
		}
		Person.apiResponseTransformer = function(responseData){
			if (angular.isArray(responseData)) {
				return responseData.map(Person.build);
			} else {
				return Person.build(responseData);
			}
		}

		// Calculated properties
		Object.defineProperty(Person.prototype, "fullName", {
			get: function() {
				return this.firstName+' '+this.lastName;
			}
		});
		Object.defineProperty(Person.prototype, "fullAddress", {
			get: function() {
				return this.addr1+', '+this.city+', '+this.state;
			}
		});
		Object.defineProperty(Person.prototype, "isFavorite", {
			get: function() {
				return this._isFavorite;
			},
			set: function(isFavorite){
				this._isFavorite = isFavorite;
			}
		});

		return Person;
	}
model)
;
```




###Templates
* **DEFINITION:** In Angular, templates are HTML.  These are typically in standalone HTML files, but can also be included as strings within the routing configuration blocks.
* **NAMING:** Filenames SHOULD be `<page-name>.tpl.html`.
* **GUIDELINES:** 
    * Use `ng-bind` for one-way binding instead of simple `{{ }}`.
    * Use `ng-cloak` to hide an element until the binding has occurred.  This will prevent flickering.
    * Use `ng-if` to remove an element completely from the DOM and `ng-show`/`ng-hide` when you need to toggle the CSS display property to show and hide content.  This is especially useful when not wanting to validate the fields being hidden.  (ng-show will continue to have active validators.)
    * When you need to set the `src` of an image dynamically use `ng-src` instead of `src` with `{{}}` template.
* **EXAMPLE:** *(An AngularJS reference app will be created which will contain examples.)*

# Naming Examples Summary

| Object Type | Sample Angular Name | Sample Pathnames | Sample Module Names |
| --- | --- | --- | --- |
| Controller | `PersonDetailsCtrl` | `/app/persons/person-details.js` | `xx.personDetails` |
| Template | n/a | `/app/persons/person-details.tpl.html` | n/a |
| Service <sup>1</sup> | `PersonService` | `/common/services/person-service.js` | `xx.service.personService` |
| Filter <sup>1</sup> | `xxCentsFilter` <sup>2</sup> | `/common/filters/cents-filter.js` | `xx.filter.centsFilter` |
| Directive | `xxAlert` <sup>2</sup> | `/common/directives/alert.js` | `xx.alert` |
| Model| `Person` | `/common/models/person.js` | `xx.model.person` |

<sup>1</sup> Services and Filters are injectable objects, so I generally find it helpful to have `Service` / `Filter` in their names and Module names to make is clear what they are.
<sup>2</sup> It is a best practices to have prefix on Filters and Directives because they are elements or attributes in the HTML and this helps insure their name is unique.

# REST Calls

Async request handling is built in to Angular.  A JavaScript library (an Angular service) called [Restangular](https://github.com/mgonto/restangular) is built upon Angular's capabilities to add additional features and allow developers to add their REST functionality with minimal code.  With Restangular, you can add request and response interceptors, define a base api URL, handle errors, and much more.  

Use Restangular in your Data Access Layer (DAL).  The following is an Angular service:

```JavaScript
"use strict";
angular.module( 'xx.service.personService', [
    'restangular'
])

.factory('PersonService',  
	function(Restangular) {
		
		var PersonService = {
			retrievePersons : function(personId){
				return Restangular.one('api/persons', personId).get();
			}
			validatePerson : function(personId)
				var request = {};
				request.personId = personId;
				return Restangular.all('api/validate').post(request);⧸⧸
			}
		}
	
		return PersonService
	}
);
```
See the reference application for additional examples and learn how to setup interceptors and implement error handling.


# Caching

* Caching patterns will be defined shortly.  We especially want to cache responses from our service calls.  Like, for instance, static zip code and person information.
* For session-level cache you can use `$cacheFactory`. This should be used to cache results from requests or heavy computations.
* Restangular also has built in caching which can be used.


## Use Angular Functions and LoDash

JavaScript is a functional language.  In that mode, it pays to get familiar with [AngularJS's built in functions](http://docs.angularjs.org/api/ng/function) and the [LoDash](http://lodash.com/) library.  These little functions will simplify your code, save you days of development, and make your coding much more enjoyable.

#### Example #1
The following code...
```JavaScript
scope.pageActionHandlers = {};
for(i=0;i <options.flows.length;i++){
	scope.pageActionHandlers[options.flows[i].name] = options.flows[i].handlers;
}
```
...can be written with LoDash as...
```JavaScript
scope.pageActionHandlers = {};
_.each(options.flows, function(flow) {
    scope.pageActionHandlers[flows.name] = flows.handlers;
});

// or better yet...
scope.pageActionHandlers = _.map(options.flows, function(flow){
    return {flow.name: flow.andlers};
});
                            .
```

#### Example #2
The following code...
```JavaScript
// get first flow where flow.name = flowName
var foundFlow = undefined;
for(i=0;i<flows.length;i++){
    if(flows[i].name == flowName){
		foundFlow = flows[i];
	}
}
```
...can be with written LoDash as...
```JavaScript
var foundFlow = _.find(flows, function(flow) {
    return flow.name: flowName;
});

// or better yet...
var foundFlow = _.find(flows, {'name' : flowName});
```




#Related Technology

### Testing

There are generally accepted unit test practices in the development community which we should investigate.  The popular stack includes:

* **[Karma](http://karma-runner.github.io/0.8/index.html):**  written by the Angular team
* **[Jasmine:](https://github.com/pivotal/jasmine/)** test-runner.  Used in conjunction with Karma and Protractor.
* **[Protractor:](https://github.com/angular/protractor)** End to end test framework for AngularJS built by the Angular team.  The team is moving their E2E tests from Karma to Protractor.  Protractor can be used with only Angular apps however.
* **[More](http://stackoverflow.com/questions/300855/javascript-unit-test-tools-for-tdd)** testing tools.

[Angular Team's E2E Testing Guide](http://docs.angularjs.org/guide/dev_guide.e2e-testing)

Some Angular projects that have a great set of examples for testing are [AngularUI](https://angular-ui.github.io/) and [Angular Translate](https://github.com/angular-translate/angular-translate)




### Development Workflow and Build Process

* **Node**:  Node does a lot, but we will not be using it for the server, but for the package manager.
* **Grunt and Gulp**: Gulp is used to build, preview and test your project.  Gulp may now be the forerunner to Grunt.  Gulp has a lot of momentum, but Grunt is  well established.
* **Yoman**: Yo scaffolds out a new application, writing your Grunt configuration and pulling in relevant Grunt tasks that you might need for your build.
* **Sass and Less**: These are CSS compiliers.  Sass has the momentum right now and is my first choice.
* **Bower**: Bower is used for dependency management, so that you no longer have to manually download and manage your scripts.


