```javascript
$(function() {
  // myApp for test directive to work, ng for $compile
  var $injector = angular.injector(['ng', 'myApp']);
  $injector.invoke(function($rootScope, $compile) {
    $('body').prepend($compile('<div ng-attr-tooltip="test">Cancel</div>')($rootScope));
  });
});


/**
 * AngularHelper : Contains methods that help using angular without being in the scope of an angular controller or directive
 */
var AngularHelper = (function () {
    var AngularHelper = function () { };

    /**
     * ApplicationName : Default application name for the helper
     */
    var defaultApplicationName = "myDefaultAppName";

    /**
     * Compile : Compile html with the rootScope of an application
     *  and replace the content of a target element with the compiled html
     * @$targetDom : The dom in which the compiled html should be placed
     * @htmlToCompile : The html to compile using angular
     * @applicationName : (Optionnal) The name of the application (use the default one if empty)
     */
    AngularHelper.Compile = function ($targetDom, htmlToCompile, applicationName) {
        var $injector = angular.injector(["ng", applicationName || defaultApplicationName]);

        var ctrName = $(htmlToCompile).attr('ng-controller');

        _log(ctrName);
        var _scope = AngularHelper.getScope(ctrName);
        $injector.invoke(["$compile", "$rootScope", function ($compile, $rootScope) {
            //Get the scope of the target, use the rootScope if it does not exists
            var $scope = _scope || $targetDom.html(htmlToCompile).scope();
            $compile($targetDom)($scope || $rootScope);
            //$rootScope.$digest();
            if ($scope) {
                $scope.$digest();
                $scope.$apply();
            }

        }]);
    };

     AngularHelper.getScope = function(ctrlName) {
        let sel = 'div[ng-controller="' + ctrlName + '"]';
        return angular.element(sel).scope();
    };

    return AngularHelper;
})();


$.ajax("myTemplate.html"), {
                success : function(view){
                    //Append the template
                    $("body").append("<div id='my-template-scope'>");
                    var $targetDom = $("#my-template-scope");

                    //Compile it to bind it with angular
                    AngularHelper.Compile($targetDom, view)
       }
});
```
