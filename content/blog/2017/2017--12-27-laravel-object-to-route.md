---
title: Use object instance in route URI - Laravel
date: 2017-12-27
---

#### So, you want to use an object instance as a variable in your URI, for example:

##### Question: What is Route Model Binding
##### https://scotch.io/tutorials/cleaner-laravel-controllers-with-route-model-binding
you have an object like:

´´´
Books $book (or App\Books $book)

´´´

and you want to create a route to a URI like example.com/edit/{title}, where
$title is $book->title;

To do so you need to override the getRouteKeyName method (see the official docs
https://laravel.com/docs/5.5/routing - Customizing the Key name). And that's
because, by default, laravel will pass the object ID as parameter.

So...... aaa ..... read the docs and finish later ---> ()
