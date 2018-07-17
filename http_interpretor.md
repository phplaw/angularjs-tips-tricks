```javascript
(function() {
  angular
    .module('myModule')
    .factory('PopupOnErrorInterceptor', [$q', '$injector', Interceptor])
    .config(['$httpProvider', Configuration]);
  function Interceptor($rootScope, $q, $injector) {
    var UNPROCESSABLE = 422, SERVER_ERROR = 500;
    return {
      responseError: function(response) {
        var popup = $injector.get('popup'); 
        //[JG]: Use injector to get services you typically don't have access to due to circular references!
        if (response.status === UNPROCESSABLE) {
          popup.error('Please fix the issues and try again!', 'There\'s issues with the form.');
        }
        else if (response.status === SERVER_ERROR) {
          popup.error('Sorry, something went wrong with the server. Please contact joseph.gefroh@gmail.com if it continues.');
        }
        return $q.reject(response);
      }
    };
  }
  function Configuration($httpProvider) {
    $httpProvider.interceptors.push('PopupOnErrorInterceptor');
  }
})();
```
