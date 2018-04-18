# Laravel 5.6 - Symfony 3.4 analogy

## To whom it is addressed this lecture
The point of this analogy it's helps those PHP developer whom been working with laravel but they've never touch symfony before, this anlogy will cover API's development and full MVC monolitic site

## Considerations
- it's highly recommended to know a little about design patterns, not necessary to be a guru but at least to know about **_dependency injection_** and **_decorator_** patterns

## Website

### Routes
The routes it's way that the client makes a request to the server asking for an specific thing that he want and then, if match with a controller this will attend the request
#### Laravel
Laravel routes are defined in `laravel-project/routes/web.php`
##### This is you can declare basic route that will attended to ExampleController
`$this->get('/', 'ExampleController@index');`
`$this->post('/', 'ExampleController@store');`

##### Resource controller are declared in this way
`$this->resource('examples', 'ExampleController');`

##### For Prefix you can use something like this
```
$this->group(['namespace' => 'Dashboard', 'prefix' => 'dashboard'], function () {
    $this->get('user/profile', ['uses' => 'ExampleController@profile', 'as' => 'example.profile']);
}
```

##### If for some reason you want to use a subdomain in your routes you can use this
```
Route::domain('{account}.myapp.com')->group(function () {
    $this->get('/', 'ExampleController@index');
    $this->post('/', 'ExampleController@store');
});
```

### Controllers
As you may know the controller it's designed to attend all your http request, delegate some work to another resource (like a service) and then return an answer to the client