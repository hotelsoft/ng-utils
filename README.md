# ng-utils
###### Daily use angular filters / directives

### **ng-module-name: form.input.formatter**

#### **1. percentage-filter**
	
###### It is to show the value by appending the percentage or any other symbol passed as the filter argument 

#### **2. input-formatter-filter**

###### Often we come across the cases where we need to format the values to represent in the UI while the database or the model objects at the front end stores them unformatted for calculation/some-other-purposes.
    
##### Usage Syntax:

*	Dependency Registration in JS
    
```javascript
var module = ng.module('your-module-name', ['form.input.formatter']);
```

*	In HTML-Template *(Either of the following)*

```html
<input input-formatter="number" type="text" ng-model="your-model"/>
<input input-formatter="number:3" type="text" ng-model="your-model"/>
<input input-formatter="currency" type="text" ng-model="your-model"/>
<input input-formatter="currency:£" type="text" ng-model="your-model"/>
<input input-formatter="currency:$:2" type="text" ng-model="your-model"/>
<input input-formatter="percentage:%" type="text" ng-model="your-model"/>
<input input-formatter="percentage:#:2" type="text" ng-model="your-model"/>
```

NOTE: 	1. As per the convention I am prepending the currency symbol and appending the percentage symbol.
		2. At the time of initialisation the values from the server side are sanitised to show in the UI. for example
			3423.00 ---> `3,423` (for number and precision = any)
			3423.4300 ---> `$3,423.4` (for currency and precision = 1)
			3423.4300 ---> `3,423.43 %` (for percentage and precision = 2 or more)
			null ---> NaN ---> `0` (for number and precision = 0)
			undefined ---> NaN ---> `$0` (for currency and precision = 0)

*	Existing Minor Issues
    
	1.	The `,` can not be deleted manually inside the input box -- Which is fine for the formatted number
	2.	Currently only `percentage`, `number` and `currency` filters are supported.
	3.	...