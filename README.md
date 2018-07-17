# angularjs-tips-tricks
Repository for begginers start learning AngularJS
### Get Angular Injector
```javascript
var $injector = angular.injector();
var $http = $injector.get('$http'); //get $http service
```
