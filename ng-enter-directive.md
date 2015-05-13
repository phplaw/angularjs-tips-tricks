**Angular Enter Directive**
You need to add a directive, like this:

--------------------------------

__Javascript:__
```javascript
app.directive('ngEnter', function () {
    return function (scope, element, attrs) {
        element.bind("keydown keypress", function (event) {
            if(event.which === 13) {
                scope.$apply(function (){
                    scope.$eval(attrs.ngEnter);
                });

                event.preventDefault();
            }
        });
    };
});
```
__HTML:__
```html
<div ng-app="" ng-controller="MainCtrl">
    <input type="text" ng-enter="doSomething()">    
</div>
```

