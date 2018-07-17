# angularjs-tips-tricks
Repository for begginers start learning AngularJS
### Get Angular Injector
```javascript
var $injector = angular.injector();
var $http = $injector.get('$http'); //get $http service
```

### Change scope outside
```html
<script>
var app = angular.module('app', []);

app.controller('ctrl', ['$scope', function ($scope) {
    $scope.message = 'hello';
}]);
  
function getScope(ctrlName) {
    var sel = 'div[ng-controller="' + ctrlName + '"]';
    return angular.element(sel).scope();
}
  
</script>

<div ng-app="app" ng-controller="ctrl">
{{message}}
</div>


<script>
  var $scope = getScope('ctrl');
  $scope.message = 'goodbye';
  $scope.$apply();
</script>
```
